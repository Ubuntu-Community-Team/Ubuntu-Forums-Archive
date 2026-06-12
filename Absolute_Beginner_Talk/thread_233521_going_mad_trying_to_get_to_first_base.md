---
title: "going mad trying to get to first base"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by adrianl on 2006-08-10
I have been trying to get Linux working on my computer for over a year - I have spent many
hours trying to get it working, and I have tried with three different distributions........
I couldn't get Mandriva to work, so I bought Fedora/Red Hat - which also didn't work. Now I have been introduced to Ubuntu which loaded up okay but I can't access the net.
My Computer is a P4 and I have a Motorola (Surfboard?)Cable Modem connecting to Telstra BugPond.
Although Ubuntu loaded up on my computer easily enough, it wasn't able to recognise any of the networking hardware or software on my computer.
The person who gave me the ubuntu disk told me others have had trouble with BigPond connections and gave me some links to follow - which were way too complex for me to follow. For starters they said to 'run' things as 'root'. I don't know what to 'run' something means and I can't seem to find any sort of command line to put any of the commands in. I did find something after searching for ages in the help menu (type 'command line' in help sometime and see what comes up!)but when i put 'gconf-editor' in it did nothing. There were only buttons that saif revert or cancel - neither seemed to do anything.
So at this point I can't get on the net and I can't seem to find my way around the system well enough to be able to fix that.
I need instructions but really basic instructions to get me going.
anyone got any ideas?
Thanks
A

---

### Post by RRS on 2006-08-10
Ubuntu uses the prefix "sudo" to grant temporary root powers rather then creating an actual root user.

For instance;
```
username@computername:~$ sudo <command>
```

You'll be prompted for a password, enter the one you created for your username during installation. It won't display, simply type it in and "enter"

To access the command line environment, System>Applications>Accessories>Terminal

To view the contents of a file;
```
cat <file path>

```
To edit;
```
sudo gedit <file path>

```
Example;
```
username@computername:~$ sudo gedit /etc/filename
```

I can't offer you any specific help with your modem/ISP setup but hopefully this will help you understand any directions or tutorials you find.

---

### Post by Shortgeek on 2006-08-10
[http://www.linux.com/howtos/Motorola-Surfboard-Modem/index.shtml](http://www.linux.com/howtos/Motorola-Surfboard-Modem/index.shtml)

I didn't look at it well, because I knew I couldn't try it (I don't have a Motorola Surfboard), but I think it will work. It might give you commands, so remember what the previous poster said about terminals. That's where you paste them. And don't forget to press enter.

P.S. If it says nothing about Ubuntu, assume "Debian" means "Ubuntu".

---

### Post by steve.horsley on 2006-08-10
Some very basics. **root** is the account name of the administrator of the machine. It is the user who has full rights to do anything. But the root account is disabled so you cannot log in as root. No problem though - there are utilities that let you temporarily elevate your status to that of root, and you just use those whenever you need to.

All the instructions you are given here will be command line instructions. The reason is that is is much easier than describing click this, look for that etc. It is also easy (once the network is working) to copy/paste commands and responses in this forum. To get a "console" where you can enter commands, use the menu Accessories->Terminal.

At the terminal, you can enter normal commands, butif you need root rights to do something, prefix the command with sudo. Frinstance, to add a user fred, the command is **adduser fred** but you cannot do this because you don't have the rights. So you type **sudo adduser fred** instead. sudo will ask you for your password (to make sure it's not someone walking by while you're out getting coffee) and then do the command. Sudo won't ask for the password again for 15 minutes.

---

### Post by bimberi on 2006-08-18
Hi Adrian,

Is your Motorola Surfboard built in or external?  If external is it connected by USB?

Cheers, Dave.

---

### Post by jrjr on 2006-08-18
.

---

### Post by asfx on 2006-08-18
Also, when you use sudo <some command> it (sometimes?) asks for a password. This is your current user password. IE: the one you typed in at the login screen. 
Edit: Sorry thats already been said.. :-#

---

### Post by adrianl on 2006-08-21
I have an external modem connected via my ethernet port (little green light flashes next to where I plug it in the back of the computer).
In my research so far - one approach (apart from 'bplogin' which I can't get to work) seems to be that I could buy a router, and that BigPond then talks to the router okay and the router can talk to Ubuntu. However, I am a bit loath to pursue this solution as it doesn't really fix the fundamental problem and if I get the wrong sort of router I won't be any further down the track to ever getting linux to work.

---

### Post by steve.horsley on 2006-08-21
If it connects to your Ethernet port, then first you need to get that ethernet port working. Do you know what kind of Ethernet adapter it is?

Can you try this command (in Applications->Accessories->Terminal) and post the output?
**ifconfig**
Don't bother to post the stuff about lo0 (the internal loopback adapter), it's any other adapters listed that we're interested in.

In the meantime, anyone who knows more about how these modems work would be welcome. A modem on Ethernet??? PPPoE perhaps?

---

### Post by jrjr on 2006-08-21
.

---

### Post by adrianl on 2006-08-22
I had my computer working with a windows (XP) environment hooked up to the net with this same cable modem. From this I can work out that the modem works and that the ethernet card works.
I first ran the Ubuntu CD on this computer from the disk in the windows environment and it worked fine and could connect to the net. Then I decided to reformat the HDD and boot the computer from disk and install Unbutu from scratch. The Linux/Ubuntu system booted and installed fine but the connection to the net has never worked since. I know that:
the cable connection works
the modem works (am using this now on another computer - Windows environment)
the computer works and
the ethernet card works but somewhere a 'handshake or protocol' isn't working and I am just not sure where to find it. I am pretty sure the answer lies in the code/instructions contained in 'bplogin' but I can't seem to be able to install it or get it to work somehow.

---

### Post by bimberi on 2006-08-22
Hi Adrian,

Got your PM thanks.  Best to work in here because if we nut this out it will benefit others :) .

Type the command **ifconfig** in a terminal.  Here's part of the output when I do it:
```
eth0      Link encap:Ethernet  HWaddr 00:0B:DB:D9:D3:1E
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20b:dbff:fed9:d31e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1487 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1489 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:1121800 (1.0 MiB)  TX bytes:180895 (176.6 KiB)
```
Do you have something similar.  In particular:

[LIST]
[*]Does it have a line starting with "eth0"?
[*]Does the block of text after it include a bit with "inet addr:nnn.nnn.nnn.nnn"?
[/LIST]Also:
[LIST]
[*]What model of Motorola Surfboard is it?
[/LIST]
Cheers, Dave.

---

### Post by adrianl on 2006-08-24
Dave,
I did the 'ifconfig' command and got the eth0 set of information. It looked very much like the one you sent me with an inet addr; 138.217.32.89 Bcast 255.255.255.255 Mask 255.255.252.0 and,
inet6 addr fe80::250 8bff:fef0 12b0/64 Scope:link

and most of the other stuff was the same as yours.
Then there was another little block after the eth0 displayed called
lo (The l character was a little different than this font) and it looked like the ethO stuff but it says     link encap: local Loopback
Hopefully this makes some sense to you.
My Motorola Surfboard modem is the one that came supplied with my Telstra Bigpond cable it is an; 'SB 5100i'
over to you........
Cheers
Adrian

---

### Post by bimberi on 2006-08-25
Hi Adrian,

Great.  All that looks good.  Hopefully what follows will just work.  I'm working from the bpalogin tutorial at
  [http://bpalogin.sourceforge.net/index.php?page=tutorial](http://bpalogin.sourceforge.net/index.php?page=tutorial)

It says that typing the command **ftp dce-server** should work, which is that it connects to that machine (and perhaps asks you to log in).  Failure would be if you get a message like "Unknown host" or something.  Whether it works or not you can type <CTRL>-C to get back to the shell prompt.

Now you need to install bpalogin.  It's actually on the Ubuntu CD!.  Put it in (hit Cancel if it asks about starting the package manager) and navigate to the pool/main/b/bpalogin directory.  Double-click on the file (bpalogin_2.0.2-6ubuntu1_i386.deb) to start the installation process.

Once installed, edit /etc/bpalogin.conf (as per the tutorial) with **sudo gedit /etc/bpalogin.conf**. Replace the relevent bits with your username and password, then save and exit.  Now do **sudo /etc/init.d/bpalogin start**.  If that looks like it has worked type **ping google.com**.  If you see lines starting with "64 bytes from 64.233.187.99" we are there! Again use <CTRL>-C to stop the pinging.

Good luck.  If this process fails somewhere post back here with the error message(s) and we'll take it from there.

Cheers, Dave.

PS. "lo" is the loopback interface - which isn't important for this exercise but definitely an important part of the networking setup.

---

### Post by adrianl on 2006-09-03
Dave,
thanks for that,
did the 'ftp dce-server' command and it seemed to work okay - well, it didn't come back with any error message.
I was then able to install bpalogin as per your instructions from the Ubuntu CD, and that seemed to work too.
Then,when I tried to edit bpalogin and put my email user details in, I got errors.
When I entered the 'sudo gedit/etc/bpalogin.conf' command on the command line I got a 'command not found response. I double checked it and did it a couple of times and each time the same response.
Any thoughts where it might have gone wrong?

Cheers
A

---

### Post by pufuwozu on 2006-09-03
> **adrianl said:**
> 'sudo gedit/etc/bpalogin.conf'If that's exactly how you put it then it's wrong. There's a space in between gedit and /etc/bpalogin.conf

Don't worry, Telstra is right on the tail of ditching the hearbeat so that means you won't need BPAlogin to be able to access the Internet.

Expect it to be totally gone in a few months.

---

### Post by adrianl on 2006-09-04
Thanks Pufuwozu,
I'll give that a try. It is getting more than tedious every time i have to give up (in despair for the umpteenth time)on the linux environment because then I have to switch over all the peripherals to my Windows machine, reset the modem and boot up to get online just to find out what to do next. And it can be as simple as a one space syntax error.
Don't you hate that!
Oh well, here goes again, shut down, switch over etc. etc. I dream of the day when i can just boot Linux and get access to the web first off - and now you tell me it might all have been in vain 'cos Big Pond might change their system
Don't you hate that too!
Anyway, i will keep at it
Cheers
A

---

### Post by bimberi on 2006-10-05
Telstra is currently making changes to their cable service which should mean this rigmorale is no longer required :) .

[http://forums.whirlpool.net.au/forum-replies.cfm?t=580901](http://forums.whirlpool.net.au/forum-replies.cfm?t=580901)

---

