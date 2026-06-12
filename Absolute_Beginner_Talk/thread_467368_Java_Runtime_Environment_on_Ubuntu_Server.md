---
title: "Java Runtime Environment on Ubuntu Server"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by One_of_Six on 2007-06-07
Hi there.

As an absolute beginner with Linux, I have managed to install the server 6.06 software and activated, Samba, Apache, jsftpd and Surgemail. So far, so good - it all works!

The next thing I want to do is run a small proxy server for a piece of amateur radio software called Echolink Proxy. This requires Java Runtime Environment to be installed.

To check if Java was installed, I logged on as root and typed"java -version" at the command line. 

The response was:

bash: java: command not found

I assumed Java was not installed so went to the Java website and downloaded the file "jre-6u1-linux-i586.bin" I followed the installation instructions on the Java website and everything went as described - no error messages and the installation finished with the line "Done." There is now a directory called  /usr/local/java/jre1.6.0_01  with files in it.

However, when I enter "java -version"

I still get

bash: java: command not found

So, before moving on to install the proxy software, is there something more I should do to activate Java?

Please remember that I am installing Java on Ubuntu Server, not Ubuntu Desktop so am working with command line only - no GUI.

Mant thanks.

---

### Post by taurus on 2007-06-07
You now need to configure it with

```
sudo update-alternatives --config java
```

---

### Post by mlind on 2007-06-07
This wiki entry about java could provide to be useful
[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by One_of_Six on 2007-06-07
> **taurus said:**
> You now need to configure it with

```
sudo update-alternatives --config java
```

unfortunately, using the suggested command results in :

"No alternatives for java."

---

### Post by taurus on 2007-06-07
What's the output of this command then?

```
ls -la /usr/local/java/jre1.6.0_01/bin
```

---

### Post by One_of_Six on 2007-06-07
> **taurus said:**
> What's the output of this command then?

```
ls -la /usr/local/java/jre1.6.0_01/bin
```


tom@server2:~$ ls -la /usr/local/java/jre1.6.0_01/bin
total 748
drwxr-xr-x 2 root root   4096 2007-03-14 10:56 .
drwxr-xr-x 8 root root   4096 2007-06-07 21:21 ..
lrwxrwxrwx 1 root root     10 2007-06-07 21:21 ControlPanel -> ./jcontrol
-rwxr-xr-x 1 root root  47116 2007-03-14 09:22 java
-rwxr-xr-x 1 root root  24886 2007-03-14 09:24 java_vm
-rwxr-xr-x 1 root root  74551 2007-03-14 09:24 javaws
-rwxr-xr-x 1 root root   6347 2007-03-14 09:24 jcontrol
-rwxr-xr-x 1 root root  47255 2007-03-14 09:22 keytool
-rwxr-xr-x 1 root root  47487 2007-03-14 09:22 orbd
-rwxr-xr-x 1 root root  47323 2007-03-14 09:22 pack200
-rwxr-xr-x 1 root root  47615 2007-03-14 09:22 policytool
-rwxr-xr-x 1 root root  47255 2007-03-14 09:22 rmid
-rwxr-xr-x 1 root root  47255 2007-03-14 09:22 rmiregistry
-rwxr-xr-x 1 root root  47251 2007-03-14 09:22 servertool
-rwxr-xr-x 1 root root  47487 2007-03-14 09:22 tnameserv
-rwxr-xr-x 1 root root 189268 2007-03-14 09:22 unpack200
tom@server2:~$

---

### Post by taurus on 2007-06-07
Try

```
sudo ln -s /usr/local/java/jre1.6.0_01/bin/java  /usr/local/bin/java
java -version
```

---

### Post by One_of_Six on 2007-06-08
Thanks, Taurus, that last instruction did the trick and Java is reporting its version.

I have one last question:

The software I want to run is a single file called "EchoLinkProxy.jar" and its configuration file called "ELProxy.conf"

The instructions given by its author simply state

"Copy both of these files to some convenient directory or folder on the PC"

then

To start the EchoLink Proxy software, open a command prompt, change to the directory or folder that contains EchoLinkProxy.jar, and type this command:

"java -jar EchoLinkProxy.jar"

So, as root, I have created a directory "/usr/local/echolink". I put the two filies in then ran the start command - and it worked fine!

What I now want to do is make the start command line run automatically whenever the server boots. Can you tell me how this can be achieved? I have tried to find out by reading some help files but, so far, I haven't achieved success.

Many thanks

---

### Post by One_of_Six on 2007-06-08
Ahh, I spoke too soon!

I've just realised that when I start the EchLinkProxy.jar program manually as above, several lines of text appear telling me that it is functioning but after they appear, I don't get a prompt back.

---

