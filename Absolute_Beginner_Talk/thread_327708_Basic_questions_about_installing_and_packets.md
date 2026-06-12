---
title: "Basic questions about installing and packets"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by durus on 2006-12-29
Hi i have some basic questions.

1. Can you post a link to a tutorial about how to install linux applications from source code ? 
2. If i install something from source code, will the packet handler in ubuntu recognize them if they fix a packet for that application later ?
3. If i install an application like amsn from the packet manager will the packet manager tell me when there is an update available as packet.
4. Can i download packet from private homepage and install them in ubuntu and will the packet manager recognize it when they adds that packet?
5. How can i see witch programs i have installed ?
6. How can i see witch programs that are running ?
7. Do i need a firewall or is that only important if i open a port ?
8. How can i mount home/aUsername to another partition ? 
I want to have my personal user files saved at hda5/aFolder. hda5 is a FAT32 partition so i can access the files from windows.
9. Why is it so many "How to install..." guides for every singe program at [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) ? If you learn how to install a program shouldn't it be the same for the others ? 

Tank you for helping me out.

---

### Post by deadgobby on 2006-12-29
> **durus said:**
> Hi i have some basic questions.

1. Can you post a link to a tutorial about how to install linux applications from source code ? 
2. If i install something from source code, will the packet handler in ubuntu recognize them if they fix a packet for that application later ?
3. If i install an application like amsn from the packet manager will the packet manager tell me when there is an update available as packet.
4. Can i download packet from private homepage and install them in ubuntu and will the packet manager recognize it when they adds that packet?
5. How can i see witch programs i have installed ?
6. How can i see witch programs that are running ?
7. Do i need a firewall or is that only important if i open a port ?
8. How can i mount home/aUsername to another partition ? 
I want to have my personal user files saved at hda5/aFolder. hda5 is a FAT32 partition so i can access the files from windows.
9. Why is it so many "How to install..." guides for every singe program at [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy) ? If you learn how to install a program shouldn't it be the same for the others ? 

Tank you for helping me out.
 Here is a couple of links to book mark and gives a simple how to install any thing. Before you start installing from source. Check Synaptic 1st for the program.
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

You can install Firestarter through Synaptic. Ubie has one all ready in the kernal program and is updated with every upgrade or when ever needed.

---

### Post by durus on 2006-12-29
> **deadgobby said:**
> Here is a couple of links to book mark and gives a simple how to install any thing. Before you start installing from source. Check Synaptic 1st for the program.
[http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

You can install Firestarter through Synaptic. Ubie has one all ready in the kernal program and is updated with every upgrade or when ever needed.


thank you for the links but [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) didn't work.
I didn't know about aptitude and will start using it instead of apt-get. Hope someone can answer the other questions to.

---

### Post by durus on 2006-12-30
I can't understand this, if aptitude can remove all it's packages when uninstalling a program, and apt-get can't, why do every guide use apt-get ?
What is the pros of apt-get ?

---

### Post by pay on 2006-12-30
apt-get has been around for longer so they use it because they might think that aptitude isn't mature enough to use regularly, or they use it just because they are used to using it for so long.

---

### Post by durus on 2006-12-30
ok thank you for helping me out, I have another question to. 
I have been reading in the forum and seen that if people downloads a package to there computer there using this command:
```
sudo dpkg -i packagename.deb
```
Can i use aptitude instead when installing a downloaded package ? and if i can't, how does uninstalling packages works when installing with dpkg

---

### Post by Sef on 2006-12-30
> I can't understand this, if aptitude can remove all it's packages when uninstalling a program, and apt-get can't, why do every guide use apt-get ?
What is the pros of apt-get ?

Aptitude is an updated apt-get.   It works the same as apt-get, but will remove any dependencies if you uninstall.

---

### Post by pay on 2006-12-30
If you download a debian file to the desktop then you need to install it with dpkg. However you should still be able to remove it with aptitude purge package

---

