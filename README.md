# Spring Kafka

Spring Kafka integrates the Apache Kafka messaging system with the Spring ecosystem, providing an open-source framework that acts as a distributed event-streaming platform. Here are some key concepts:

- **Distributed**: Operates across multiple devices or servers.
- **Event**: Represents real-time data as it is generated.
- **Streaming Platform**: Enables the transformation and processing of data in real time.

Spring Kafka simplifies producing and consuming messages from Kafka by leveraging familiar Spring concepts like dependency injection, configuration, and annotations.

## Core Kafka Components

### Kafka Producer
The **Kafka Producer** is responsible for handling and sending data to the Kafka cluster.

### Kafka Cluster
The **Kafka Cluster** is composed of multiple Kafka brokers that work together to manage and distribute data.

### Kafka Brokers
Kafka brokers manage data storage and retrieval within a Kafka cluster. They store and organize the incoming data, distributing it as needed.

### Kafka Consumers
Kafka consumers retrieve data from the Kafka cluster. They read messages from specified topics.

### Kafka Connector
Kafka Connectors allow data to move in and out of Kafka clusters. 
- **Source**: Moves data into Kafka.
- **Sink**: Moves data out of Kafka to another system.

### Zookeeper
Zookeeper is used to manage and coordinate Kafka brokers and clusters. It handles configurations, leader elections, and cluster state.

### Kafka Stream
Kafka Streams is used for real-time data transformation and processing. It processes data between Kafka clusters and Kafka Stream applications.

---

## Kafka Topics and Partitions

- **Topic**: A Kafka topic functions similarly to a database table, storing related messages. For example, a topic named `Student` might store messages related to students.
  - A producer sends messages to a topic.
  - Topics are divided into **partitions** to enable parallel processing and scalability.

- **Partitions**:
  - Partitions divide a topic’s data into smaller, ordered segments.
  - When creating a topic, you must specify the number of partitions.
  - Each partition stores messages with unique **offset** values, representing the position of each message in that partition.
  - Partitions are processed independently, allowing for high scalability.

### Sending Messages with Command Line Runner

Messages sent to Kafka brokers are structured as **key-value pairs** (the key is optional).
- **Without a Key**: Data is distributed across partitions in a **round-robin** fashion.
- **With a Key**: Data is sent to a specific partition based on a **hash of the key**.

---

## Key Kafka Commands

### Starting Zookeeper and Kafka Server

To start the Zookeeper server and Kafka broker, use the following commands (assuming you're in the Kafka installation directory):

- **Zookeeper Start Command**:
  ```bash
  zookeeper-server-start.bat ..\..\config\zookeeper.properties

- **Kafka Server Start Command**:
  ```bash
  kafka-server-start.bat ..\..\config\server.properties
- **Create a Kafka topic Command**:
  ```bash
  kafka-topics.bat --create --topic foods --bootstrap-server localhost:9092 --replication-factor 1 --partitions 4
- **Kafka Producer Command**:
  ```bash
  kafka-console-producer.bat --broker-list localhost:9092 --topic foods --property "key.separator=-" --property "parse.key=true"
- **Kafka Consumer Command**:
  ```bash
  kafka-console-consumer.bat --bootstrap-server localhost:9092 --topic foods --from-beginning -property "key.separator=-" --property "print.key=false"
## Consumer Offset and Consumer Group

The **Consumer Offset** and **Consumer Group** are key to understanding how Spring Kafka manages and tracks data.

### Difference Between Consumer Offset and Consumer Group

- **Consumer Offset**: Represents the latest data that a consumer has read, enabling Kafka to keep track of processed data.

- **Consumer Group**: A group that coordinates multiple consumers to read messages from a topic, with each message being read by only one consumer in the group.


