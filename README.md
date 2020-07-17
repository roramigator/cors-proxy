# CORS proxy
Avoid CORS errors on a development environment.

## Getting started
Follow these instructions to setup the server on your local machine.

### Prerequisites
You'll need [Node](https://nodejs.org/en/about/releases/) to run the server.

You can have the repository anywhere in your system but I suggest placing it *within your project directory* and adding it to the *.gitignore* file.

```sh
cd ~/path/to/my/project
git clone https://github.com/roramigator/cors-proxy
echo "cors-proxy" >> .gitignore
```

### Dependencies
Install them with `npm`.

```sh
cd cors-proxy
npm install
```

Once installed you can run the server like so:

```sh
npm run proxy
```

### Usage
Now, the server is running on `http://localhost:7000` and you can make requests; to do it you have to pass a *string* containing the API *url* as a variable, identifying it as **url**:

```javascript
const myURL = "https://api.roramigator.dev/countries";

fetch(`http://localhost:7000/?url=${myURL}`) // ...url=https://api.roramigator.dev/countries
  .then(set => set.json())
  .then(response => console.log(response));
```

If the API's response is JSON it would parse and return it.

```json
["US","RU","NP","IN","VE","..."]
```

If the *url* does not respond with a JSON [`http://localhost:7000/?url=https://roramigator.dev`], it will return an object indicating the status.

```json
{
"type": "error",
"message": "could not parse response",
"response": "<!DOCTYPE html>\n<html lang='en'>\n<head> ... ... ..."
}

```

---
:thumbsup:
