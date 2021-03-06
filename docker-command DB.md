# Database commands
	
**create docker network**
	Docker network create mongo-network
	
**start mongodb**

	docker run -d \
	-p 27017:27017 \
	-e MONGO_INITDB_ROOT_USERNAME=admin \
	-e MONGO_INITDB_ROOT_PASSWORD=password \
	--net mongo-network \
	--name mongodb \
	mongo
	
	
**start mongodb with Persistant Volume***

	docker run -d \
	-p 27017:27017 \
	-e MONGO_INITDB_ROOT_USERNAME=admin \
	-e MONGO_INITDB_ROOT_PASSWORD=password \
	-v mongo_db:/data/db \
	--net mongo-network \
	--name mongodb \
	mongo
	
**start mongodb with Persistant Volume without username and password**

	docker run -d \
	-p 27017:27017 \
	-v mongo_db:/data/db \
	--name mongodb \
	mongo
	
**start mongo-express**

	docker run -d \
	-p 8081:8081 \
	-e ME_CONFIG_MONGODB_ADMINUSERNAME=admin \
	-e ME_CONFIG_MONGODB_ADMINPASSWORD=password \
	-e ME_CONFIG_MONGODB_SERVER=mongodb \
	--net mongo-network \
	--name mongo-express \
    mongo-express
