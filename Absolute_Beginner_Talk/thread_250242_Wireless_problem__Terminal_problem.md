---
title: "Wireless problem / Terminal problem"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by Retnuh on 2006-09-03
I have the internet connected through my ethernet cable, but I do not have wireless.

I looked in the Network Settings and do not see wireless as one of my connections. Just Modem, which is not active, and Ethernet which is active.

I am currently trying to solve the problem on my own, which is the way I see as learning Linux. Reading and trying to institute what I have learned to solve me problems.

I am a noob to Linux/Ubuntu and just installed it last night. Everything that is said in these forums is giberish to me. I like this though, and will stick with it.

Here is my problem/s.

I have been reading on: [http://help.ubuntu.com/community/wifidocs/wirelesstroubleshootingguide]("http://help.ubuntu.com/community/wifidocs/wirelesstroubleshootingguide")

I found where I can input into the terminal some codes to try to find out what my problem is. I saw that I could type the following code and find out if my wireless card has a driver, or is even found y the system.

```
sudo lshw
```



I was able to do this one time, and now if I type this code it gets hung up on the "IDE", it doesnt finish with the results. Just locks up.

I then found that I could find out info of the bus by typing:

```
sudo lshw -businfo
```



I did this once, but have not done it again.

I tried looking at the network class to take a closer look at my wireless card / driver by typing:

```
sudo lshw -class
```


This was my result:

```
retnuh@retnuh-laptop:~$ sudo lshw -class network
IDE

```

As you can see it gets locked up on IDE. It did tell me once before some information, but it did not have any bus info. So I was reading that it might not have a driver installed.



How do I fix this IDE lock up thing in my Terminal?

What should I do about my wireless problem?


I am currently reading up on how to install programs or files into Ubuntu. I do not know how to do this yet, and I know that I will more than likely have to dl and install a driver for my
NetGear WG511 v2
54 Mbps Wireless PC Card


Thanks for the Help in advance.

---

### Post by Retnuh on 2006-09-03
bump*

Does anyone know?

---

### Post by NetworkGuy on 2006-09-03
According to the Wiki, your card is supported but you will need to use NDISWRAPPER to get this card running.

Take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=76804](http://ubuntuforums.org/showthread.php?t=76804)

It's for a earlier version of Ubuntu

---

### Post by Retnuh on 2006-09-03
I just saw this and I have no idea what it means.
add a line? wtf lol 

Someone please help me. I am posting the suggestion below what I read and am trying to accomplish.
I am trying to fix wireless, and am on the website listed above by NetworkGuy.

Also, add a line containing the following to the /etc/hotplug/blacklist file using your favorite text editor (must have root privelages).

Code:

prism54

---

### Post by aaronbeekay on 2006-09-03
"Add a line" means add the text in a new line at the end of the file located in /etc/hotplug/blacklist. You can use any text editor you like, one easy one is gedit.

So the command to run would be

sudo gedit /etc/hotplug/blacklist

The sudo gives you superuser privileges (meaning you can edit anything), the gedit launches gedit, and /etc/hotplug/blacklist is the file to open.

Simply add "prism54" to the end of the document and save it.

---

### Post by Retnuh on 2006-09-03
I have entered "sudo gedit /etc/hotplug/blacklist" and it opens gedit, but there is no information in it. So the beginning and the end are the same. LOL

Now what?

---

