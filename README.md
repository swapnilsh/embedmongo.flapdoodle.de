# Embedded MongoDB

Embedded MongoDB will provide a platform neutral way for running mongodb in unittests

## Why?

easy access??

## Howto

### Maven

Stable (not yet)

	<dependency>
	  <groupId>de.flapdoodle.embedmongo</groupId>
		<artifactId>de.flapdoodle.embedmongo</artifactId>
	  <version>1.0</version>
	</dependency>

Snapshots (Repository http://oss.sonatype.org/content/repositories/snapshots)

	<dependency>
	  <groupId>de.flapdoodle.mongoom</groupId>
		<artifactId>de.flapdoodle.mongoom</artifactId>
	  <version>1.0-SNAPSHOT</version>
	</dependency>


### Usage

	int port = 12345;
	MongodProcess mongod = null;

	try {
		mongod = EmbeddedMongoDB.start(new MongodConfig(Version.V1_6_5, port));

		Mongo mongo = new Mongo("localhost", port);
		DB db = mongo.getDB("test");
		DBCollection col = db.createCollection("testCol", new BasicDBObject());
		col.save(new BasicDBObject("testDoc", new Date()));

	} finally {
		if (mongod != null)	mongod.stop();
	}


