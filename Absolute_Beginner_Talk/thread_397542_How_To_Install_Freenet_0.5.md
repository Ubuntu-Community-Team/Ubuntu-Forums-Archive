---
title: "How To: Install Freenet 0.5"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by InTheFlow on 2007-03-30
Does anyone know how to install Freenet version 0.5 on Ubuntu Edgy Eft?  I looked in Synaptic Package Manager using multiverse universe and restricted options but don't find it. I then tried to do it the manual way by downloading the tar file but when running "sh start-freenet.sh" I get a bunch of directory not found messages.

If I type in: "java -version" I get:

" java version "1.5.0_08"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_08-b03)
Java HotSpot(TM) Client VM (build 1.5.0_08-b03, mixed mode, sharing)

So I think I have the correct version of Java installed.
Any help would be appreciated. Thanks!

---

### Post by pay on 2007-03-30
You might need to run it as super user... but i might be wrong.

---

### Post by InTheFlow on 2007-03-30
How do you run as a super user?

---

### Post by %hMa@?b&lt;C on 2007-03-30
> **InTheFlow said:**
> How do you run as a super user?

sudo [command that you want to run]

---

### Post by InTheFlow on 2007-03-30
Thanks. I'll try that after I can get the download again. It seems that the freenet webpage is down at the moment and I can't find the file I downloaded earlier.

Do files in the /TMP directory get erased automatically after a certain amount of time?

---

### Post by InTheFlow on 2007-03-31
Well, I tried executing it with and without sudo:

sh start-freenet.sh
sudo sh start-freenet.sh

Both commands give me the same stuff below:

Detected freenet-ext.jar
Detected freenet.jar
Sun java detected.
head: error while loading shared libraries: libc.so.6: cannot open shared object
 file: No such file or directory
sed: error while loading shared libraries: libc.so.6: cannot open shared object 
file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object
 file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object
 file: No such file or directory
grep: error while loading shared libraries: libc.so.6: cannot open shared object
 file: No such file or directory
Sun Java 1.4.2 detected.
uname: error while loading shared libraries: libc.so.6: cannot open shared objec
t file: No such file or directory
test: 159: Darwin: unexpected operator
Starting Freenet now: Command line: java -Xmx128m freenet.node.Main
nice: error while loading shared libraries: libc.so.6: cannot open shared object
 file: No such file or directory
Done

So it is obviously ticked that it can't find some directories or files but the question is which ones? Any ideas? :confused: 

Thanks!

Edit: Ok, it seems to be looking for the libc.so.6 file. Well, I checked and that file is on my file system in the /bin directory and there is one in the /lib/tls/i686/cmov directory as well. They are different sizes though. One is 1.1 MB and the other is 1.2 MB. The 1.2MB one is a tad bit newer than the other one.

---

### Post by pay on 2007-03-31
I don't think that a file like that is suppose to be in the /bin directory

---

### Post by InTheFlow on 2007-04-01
I tracked down a person that knows a lot more about freenet and linux than I do (Thanks urza!) and he recommended that I change the following in my start-freenet.sh file:

if test -f /etc/redhat-release
then
LD_ASSUME_KERNEL=2.2.5
export LD_ASSUME_KERNEL
#gentoo however dies with 2.2.5
elif test -f /etc/gentoo-release -o -f /etc/SuSE-release
then
LD_ASSUME_KERNEL=2.4.1
export LD_ASSUME_KERNEL
else
LD_ASSUME_KERNEL=2.2.5
export LD_ASSUME_KERNEL
fi


with just:

LD_ASSUME_KERNEL=2.6.17

That made all the file not found errors go away for me. So, if you are having the same problem, do the above except put your own kernel version number in there. You can find out what kernel version you have by typing "uname -r" in a terminal window. (Thanks mikewhatever!)

Now I'm getting the following error:

test: 147: ==: unexpected operator

Not sure if that is a problem but I haven't gotten freenet running yet so it probably is. ;)

---

