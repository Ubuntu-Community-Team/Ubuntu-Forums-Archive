---
title: "[SOLVED] Java error while running openfire"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by sajiv_k on 2007-12-12
I have installed open fire using instructions from [here]("http://ubuntu-unleashed.blogspot.com/search/label/Install%20Jabber%20Server%20on%20Ubuntu")

But when I try to run it I get this error message

> Starting openfire
nohup: appending output to `nohup.out'
nohup: cannot run command `/etc/env.d/java/20sun-jre-bin-1.5.0.06/bin/java': No such file or directory


and [http://localhost:9090](http://localhost:9090) gives me a server not found.

---

### Post by kpkeerthi on 2007-12-12
Apparently it is trying to locate java from a wrong path. Unfortunately, I'm unable to access the website you provided as my proxy is blocking it. Edit the file that you are running to start open fire and replace `/etc/env.d/java/20sun-jre-bin-1.5.0.06/bin/java' to java.
I assume you have java installed. Is
```

java -version

```
printing the version information?

---

### Post by sajiv_k on 2007-12-12
Tried that.

It gave me this error

> nohup: appending output to `nohup.out'
nohup: cannot run command `java/bin/java': No such file or directory

Then I remembered that the tutorial said 

> Set java6 as your default.
Code:
$ sudo update-alternatives --config java
select /usr/lib/jvm/java-6-sun/jre/bin/java

So I replaced with this new path

I get this error now

> nohup: appending output to `nohup.out'
nohup: cannot run command `/usr/lib/jvm/java-6-sun/jre/bin/java/bin/java': Not a directory


java -version gives me this 

> Set java6 as your default.
Code:
$ sudo update-alternatives --config java
select /usr/lib/jvm/java-6-sun/jre/bin/java

---

### Post by sajiv_k on 2007-12-12
It worked.

After posting I noticed that the error which it gave was

nohup: cannot run command `/usr/lib/jvm/java-6-sun/jre/[COLOR="Red"]bin/java/bin/java[/COLOR]': Not a directory

the **/bin/java** was repeated, it was automatically getting added. 

So I edited the file and put in ```
/usr/lib/jvm/java-6-sun/jre/
``` and removed the rest.

---

### Post by kpkeerthi on 2007-12-12
> 
java -version gives me this 

Quote:
Set java6 as your default.
Code:
$ sudo update-alternatives --config java
select /usr/lib/jvm/java-6-sun/jre/bin/java  


Are you sure java -version printed that? Which file did you replace? Would you mind posting the content of that file here? I'll take a look.

---

### Post by sajiv_k on 2007-12-12
Sorry for the pasting error

java -version gave this

> java version "1.6.0_03"
Java(TM) SE Runtime Environment (build 1.6.0_03-b05)
Java HotSpot(TM) Client VM (build 1.6.0_03-b05, mixed mode, sharing)

I edited the openfire file and replaced the **app_java_home** with the path where Java was installed

```
app_java_home=/usr/lib/jvm/java-6-sun/jre
```

---

