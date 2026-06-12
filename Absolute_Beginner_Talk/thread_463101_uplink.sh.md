---
title: "uplink.sh ???"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by lsalminen on 2007-06-03
Hi,

I downloaded the Uplink linux trial file from their website (it's a game), and it downloaded as "uplink-demo-1.54.sh". When I double click, gedit says "Could not open the file /home/lee/Desktop/uplink-demo-1.54.sh."

What do you do with a .sh file?

Thanks, Lee

I also tried unzip in terminal...forgot to put that in the original post

---

### Post by taurus on 2007-06-03
Applications -> Accessories -> Terminal
```
cd ~/Desktop
sh ./uplink-demo-1.54.sh
```

---

### Post by dbott67 on 2007-06-03
Warning: Be careful when running untrusted scripts.

On to the problem.  In order to 'execute' a file, it must be set to 'executable', so you need to perform these steps:

1. Open a terminal.
2. Copy & paste (or type) the following command:
```
chmod +x /home/lee/Desktop/uplink-demo-1.54.sh
```3. Change to the directory where the script resides:
```
cd ~/Desktop
```4. Run the file:
```
./uplink-demo-1.54.sh
```Note: the script needs to be prefaced by a [COLOR=Red]**./**[/COLOR] in order to be run.  By default, only scripts that are located in directories that are part of the PATH environmental variable can run without using the ./.

For example, on a default Feisty installation, the default PATH environmental variable only includes these directories:
```
dbott@feisty:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

-Dave

---

### Post by Ritz Cracker on 2008-06-29
I know this is a old thread, but I think it does belong here.

I get this error when trying to run the uplink-demo-1.54.sh : 

RitzCracker@laptop:~$ chmod +x /home/larsove/Desktop/uplink-demo-1.54.sh
RitzCracker@laptop:~$ cd ~/Desktop
RitzCracker@laptop:~/Desktop$ ./uplink-demo-1.54.sh
Verifying archive integrity... All good.
Uncompressing Uplink demo 1.54DEMO...........................................................................................
/home/RitzCracker/.setup8444: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory
RitzCracker@laptop:~/Desktop$ 

Any chance to get some help? I`m running Ubuntu Linux 8.04 LTS 32bit Desktop edition.

---

### Post by forger on 2008-06-29
You're missing libgtk-1.2
> sudo apt-get install libgtk1.2

---

### Post by Ritz Cracker on 2008-06-29
> **forger said:**
> You're missing libgtk-1.2

okey :) I will try that now ;)

Thanks for the fast answer :D

Edit: It works now :D

---

