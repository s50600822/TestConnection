# TestConnection
Poke Poke Poke


#How to

## poking a troublesome connection
```
# compile
javac TestConnection.java

# run
java TestConnection "https://google.com"

# to troubleshoot Handshake, connection
java -Djavax.net.debug=all TestConnection "https://google.com"

# specific protocol
java -Dhttps.protocols=TLSv1.2,TLSv1.1,TLSv1  -Djavax.net.debug=all "https://google.com"
```

## plug and play
- you are in container like adoptopenjdk/openjdk11 where there's
- you can't commit .class (per usual git ignore)
- want to plug and play

package it
```
javac TestConnection.java
jar -cf  TestConnection.jar TestConnection.class
```

run
```
java  -cp TestConnection.jar TestConnection "https://google.com"
java  -Djavax.net.debug=all -cp TestConnection.jar TestConnection "https://google.com"
...
```

## some useful command to cross check:
```

openssl s_client -showcerts -connect google.com:443

curl -vvL -k "https://google.com"

keytool -v -list -keystore ~/.sdkman/candidates/java/11.0.11.hs-adpt/lib/security/cacerts
```
