---
title: "Java &amp; Ubuntu Server"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by One_of_Six on 2007-06-25
I am running an Ubuntu Server 6.06

I have java installed and when running a .jar program use the command:

java -jar *filename*.jar

I want to run *filename*.jar at boot up and have written a script with the line: "java -jar *filename*.jar" in the init.d directory

At boot up, when the script is run, the error message "java command not found" is returned.

My question is:

When manually entering java -jar *filename*.jar in a console, *filename*.jar starts ok

When java -jar *filename*.jar is attempted in a script during boot up, the java command is not recognised. I have given the script symlink an order number which causes it to be read after all the other boot up commands except the final login have been actioned . Is there something I have missed?

---

### Post by lamalex on 2007-06-25
have you tried running the script manually to make sure it works? paste your script here if it doesn't work and we'll help.

---

### Post by One_of_Six on 2007-06-25
Thanks

The script is called "RunEchoLink" and is in the /etc/init.d directory. It contains the 2 lines:

#!/bin/sh
java -jar /usr/local/echolink/EchoLinkProxy.jar

it's permissions are:

-rwxr-xr-x 1 root root 59 2007-06-24 18:06 RunEchoLink

There is a symlink in rc2.d called S92RunEchoLink

By running it manually, I presume you mean going to the /etc/init.d directory and typing "RunEchoLink"?

I did that and was told:

-bash: RunEchoLink: command not found

As you can see, I'm very much at the start of the Linux learning curve. I have managed to set up the server with mail, ftp and apache etc . However this problem is becomming a bit wearing!

---

