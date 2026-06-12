---
title: "MyTunesRSS Script"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by patchmonkey on 2007-06-07
Hi,
I am trying to get MyTunesRSS (platform independent) to run as a clickable script.

If I type this into terminal ```
- java -Xms32m -Xmx128m -Xbootclasspath/p:lib/codewave-zis.jar -Djavax.xml.parsers.SAXParserFactory=org.apache.xerces.jaxp.SAXParserFactoryImpl -jar MyTunesRSS.jar -debug
``` in /MyTunesRSS-3.0-rc6, it runs fine and launches the server.

I made an executable file on the desktop that had this: ```
java -Xms32m -Xmx128m -Xbootclasspath/p:lib/codewave-zis.jar -Djavax.xml.parsers.SAXParserFactory=org.apache.xerces.jaxp.SAXParserFactoryImpl -jar ./MyTunesRSS-3.0-rc6/MyTunesRSS.jar -debug
``` in it, but it always fails when launching the server - the program will run, but it can't start the server.

Any help is appreciated!

---

### Post by homelessfreak on 2007-06-10
The reason the  you cant start the server is because you have to be working from the folder MyTunesRSS is in when lauching the program, i have got around this with a small script...

cd /media/External/Linux/MyTunesRSS-3.0-rc6/

/usr/lib/jvm/java-6-sun/bin/java -Xms32m -Xmx128m -Xbootclasspath/p:lib/codewave-zis.jar -Djavax.xml.parsers.SAXParserFactory=org.apache.xerces.jaxp.SAXParserFactoryImpl -jar /media/External/Linux/MyTunesRSS-3.0-rc6/MyTunesRSS.jar -debug


you have to change the folder address and stuff but it works for me

---

