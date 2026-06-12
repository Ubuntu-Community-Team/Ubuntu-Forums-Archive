---
title: "No Problems just Questions"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-21
I have just installed Linux-686 and have verified it is running. I don't notice any change from 386.
Some  things i don't understand .

To install linux-686 I first used the following command.

    ```
   sudo apt-get update
   sudo apt-get install  linux-686
```


           After a re-boot  i had 686 installed.

I then did the following, don't ask why because I don't know except I saw it somewhere where you are supposed to run update and then upgrade.
 [B] ```

       sudo apt-get upgrade  
 
```[/B]
 Can someone tell me what exactly the update command does and what the upgrade command did.

  What is the difference ? And does it make a difference I did them in the wrong order ?

Thanks for any info

---

### Post by gord on 2006-02-21
update gets a list of all the packages available so that you can search through them (with synaptic or whatever, allthough that does apt-get update in the background)

i beleve upgrade upgrades all of your packages that are out of date.

---

### Post by nalmeth on 2006-02-22
check this link out --> [http://www.die.net/doc/linux/man/man8/apt-get.8.html](http://www.die.net/doc/linux/man/man8/apt-get.8.html)
it refers to debian, which ubuntu is built on.

EDIT:
I just googled to find this. For more in depth info just search debian or apt or apt-get etc
or wiki
[http://en.wikipedia.org/wiki/Apt-get](http://en.wikipedia.org/wiki/Apt-get)

---

### Post by kent41 on 2006-02-22
nalmeth

 Thanks for the link, it is just what I was looking for. It will be very helpful.

Thanks

Kent\\:D/

---

