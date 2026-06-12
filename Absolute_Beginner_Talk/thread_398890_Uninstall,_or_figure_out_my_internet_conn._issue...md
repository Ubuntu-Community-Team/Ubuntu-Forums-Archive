---
title: "Uninstall, or figure out my internet conn. issue.."
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by ChrisCourtney2610 on 2007-04-01
I have a lap top that I just got and after a couple of weeks of trying to get used to Ubuntu, I've decided I can't do it. I've read, and read, yet have been unable to find a way to uninstall it. Ubuntu is the only OS on the computer. I just want to remove it completely, and install Windows... Please help out. I primarily got this lap top for one reason only- to access the internet. And I have yet to be able to do that with the exception of one time. It shows that the connection is strong, but it say's that it's disconnected. If I could get online, then I would keep Ubuntu, because I want to learn to use it, but it's just getting on my nerves, and at this point, I just want to go back to what I know. Any help, either with fixing my connection "problem" or uninstalling would be greatly appreciated. Thanks in advance.

---

### Post by NeoLithium on 2007-04-01
Well; the networking problem doesn't always mean that it can't be fixed. What type did you have? Always wireless or did you use ethernet on occasion....do you use PPPoE? (Username and password required to access the internet).

I'm pretty sure some of us can get you up and running :)

---

### Post by ChrisCourtney2610 on 2007-04-01
Please HELP!!! I'm going to throw the computer through my bedroom window soon!!!!!

---

### Post by oilchangeguy on 2007-04-01
is this computer new/used, what? do you have the system restore disc?

---

### Post by ChrisCourtney2610 on 2007-04-01
Well, I just typed a reply, but it didn't post for some reason. Anyway... I have an ethernet connection which I use. I just happened to be on my patio last week just messing around trying to figure this whole thing out, and noticed I was picking up a strong signal, so I opened the browser and was able to get on any site I wanted, blah, blah, blah... So, I go inside and turn the computer off... Well the next day I hook up my ethernet cable and I don't even show a connection. I went back outside to see if I could leech off the signal again, and I was getting a strong signal, but showed that it was disconnected. I'm not wanting to leech off their signal, I'm just trying to figure everything out...

---

### Post by ChrisCourtney2610 on 2007-04-01
It's used. The only thing I have is a LiveCD I made, and I have an XP disc. I should really have made a thread titled, "I don't know what I'm doing, but if you can help me figure out Ubuntu I'll be glad to keep it and learn to use it." I don't necessarily want to get rid of Ubuntu, but I'm getting tired of not being able to do simple things that I could easily do in Windows...

---

### Post by NeoLithium on 2007-04-01
Well, with your wired connection, go into System -> Administration -> Networking.  Your wired connection should be set to DHCP if your ISP doesn't require a username and password for you to access their service, if they DO require it, you can open up a terminal window and type:
```
pppoeconf
``` And that will walk you through setting up that type of connection.

---

### Post by ChrisCourtney2610 on 2007-04-01
A username and password is not required...

---

### Post by oilchangeguy on 2007-04-01
the major draw back with most versions of linux is they have a large learning curve, when compaired to windows. but just remember when you were new to windows, there was a lot to learn, ubuntu is no different. and the ubuntu forum is by far the best linux forum on the net. so give ubuntu a try, there's lots of help here.

---

### Post by spacedogg on 2007-04-01
Ok Chris, I know how you feel because I felt the same way. 

From what I understand, you personally don't have wireless internet at your house, is that correct? But you did take your laptop outside and got a signal so you opened up your browser, and you were able to get connect to the internet without any problems. 

You may not have a "signal" with an ethernet connection. Did you open up your browser and see if you could get anywhere?

---

### Post by ChrisCourtney2610 on 2007-04-01
It's completely foreign to me, and after two weeks of trying, I've made no advancement in navigating through it. I try and play a DVD, and I can't do it. I try to get online, and I can't do it. I'm getting so frustrated...

---

### Post by NeoLithium on 2007-04-01
Just in case, can you copy and paste the output of this command in a terminal window?
```

cat /etc/network/interfaces

```

---

### Post by ChrisCourtney2610 on 2007-04-01
> **spacedogg said:**
> 
From what I understand, you personally don't have wireless internet at your house, is that correct? But you did take your laptop outside and got a signal so you opened up your browser, and you were able to get connect to the internet without any problems. 

You may not have a "signal" with an ethernet connection. Did you open up your browser and see if you could get anywhere? Correct, I do not have wireless at my house, but went outside and picked up a signal, and was able to browse the internet. I opened my browser after hooking up my ethernet connection and nothing.

---

### Post by oilchangeguy on 2007-04-01
when you go to system, admin, networking, what's listed?

---

### Post by ChrisCourtney2610 on 2007-04-01
> **NeoLithium said:**
> Just in case, can you copy and paste the output of this command in a terminal window?
```

cat /etc/network/interfaces

``` Okay, here comes something that you may or may not laugh at-- What is a terminal window!!?!??! I think I know what you're talking about, because while messing around, I opened a window where I would have been able to enter commands in. Now, If you were to say, "Ok open that back up." My reply would be, "Uh....Yeah I don't remember how I did it." I'm super new to this, so please don't laugh or anything, I am just so lost.

---

### Post by NeoLithium on 2007-04-01
No one will laugh at you :) We all started out somewhere, and remeber how it can be! :)

Just go into Applications -> Accessories and click on terminal, the window should pop up, and you can enter the command :)

---

### Post by Maestro23 on 2007-04-01
Apps>>Accessories>>Terminal

---

### Post by ChrisCourtney2610 on 2007-04-01
Listed- [-]Wireless connection: This network interface is not configured.
                   ^^^This has changed. Did have a [check]^^^
                     --I also had two of those listed at one time--
       
           [check] Wired connection: Address: DHCP
           [-]Modem connection: This network interface is not configured.

---

### Post by ChrisCourtney2610 on 2007-04-01
okay, now I remember that. 
In the terminal window it has- "chris@chris-llaptop:~$" Do I need to remove that before entering the command?

---

### Post by Maestro23 on 2007-04-01
> **ChrisCourtney2610 said:**
> okay, now I remember that. 
In the terminal window it has- "chris@chris-llaptop:~$" Do I need to remove that before entering the command?

That's your command prompt. Enter your commands.

---

### Post by NeoLithium on 2007-04-01
Nope, you can just type the command :)

---

### Post by oilchangeguy on 2007-04-01
do you have the network mgt. icon showing to the left of the clock? (if not right click on the panel and add this to the panel) from the drop down menu in the network mgt. select eth0, and you should be able to connect then.

---

### Post by ChrisCourtney2610 on 2007-04-01
I put in the command. and i show, "auto lo- iface lo inet loopback" "iface eth0 inet dhcp" "auto eth2 iface eth2 inet dhcp" " auto ath0 iface ath0 inet dhcp" "auto wlan0 iface wlan- inet dhcp" and "auto eth0"

---

### Post by ChrisCourtney2610 on 2007-04-01
> **oilchangeguy said:**
> do you have the network mgt. icon showing to the left of the clock? (if not right click on the panel and add this to the panel) from the drop down menu in the network mgt. select eth0, and you should be able to connect then.yes i do. ethernet connection I assume, correct? Or a wireless?

---

### Post by NeoLithium on 2007-04-01
Ok, I think I might have the problem, in the terminal window type:
```

gksu gedit /etc/network/interfaces

```

And at the line that says **iface eth0 inet dhcp**, add his line above it-  **auto eth0**, then save the file.

After it's added, it should look like this:
```

auto eth0
iface eth0 inet dhcp

```
Then in the same terminal window type
```

sudo /etc/init.d/networking restart

```

---

### Post by ChrisCourtney2610 on 2007-04-01
type the "sudo..." command in the window where I edited the auto eth0 at and saved? or back to the terminal window, if in the first terminal window, it says, [fail]...

---

### Post by NeoLithium on 2007-04-01
When you type the command with gedit, it should pop up a text editor window that has the information that was displayed, add the line in that window, save, and close it. Then in the terminal window again, type the sudo /etc/init.d/networking restart

---

### Post by Maestro23 on 2007-04-01
> **ChrisCourtney2610 said:**
> type the "sudo..." command in the window where I edited the auto eth0 at and saved? or back to the terminal window, if in the first terminal window, it says, [fail]...

sudo commands at the terminal prompt.

Edit: Neo beat me to it.  I will just sit back and watch now...LOL

---

### Post by ChrisCourtney2610 on 2007-04-01
argh!!!! [[COLOR="Red"]fail[/COLOR]]

---

### Post by NeoLithium on 2007-04-01
Which command does it say fail after?

---

### Post by ChrisCourtney2610 on 2007-04-01
"sudo /etc/init.d/networking restart" and below it, "* reonfiguring network interfaces... /etc/network/interfaces:22: interface eth0 declared allow-auto twice ifdoen: couldn't read interfaces file "/etc/network/interfaces" and the same thing after "ifup:"

---

### Post by ChrisCourtney2610 on 2007-04-01
Well, thanks for helping, but I've got somewhere to be, but I'll be back later to try and figure this out. Thanks!!!   Linux>me

---

### Post by ChrisCourtney2610 on 2007-04-01
Okay, I'm back for round two...

---

