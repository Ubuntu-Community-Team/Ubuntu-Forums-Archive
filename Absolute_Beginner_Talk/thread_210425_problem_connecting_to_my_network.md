---
title: "problem connecting to my network"
date: 2006-07-06
forum: Absolute Beginner Talk
---

### Post by LetUrSensesFail1 on 2006-07-06
my problem is this: when i use the live CD, my internet connection works and i can use firefox, but after i installed ubuntu on my hard drive, i can not connect to the internet at all. when i go to "system - administartion - networking" it shows the "eth0" as being active. i tried all the basic things i could think of, like disableing, and then re-activating, but nothing worked. my thought is that i am missing a driver for the network card. i downloaded a driver from my windows computer. the dirver says that it it linux compatable, but the readme tells me to compile files (among other things) and being new to linux and ubuntu, im not sure on how to do this. 

can someone please help me with either the entire connection problem or at least on how to compile a file?

---

### Post by batholith on 2006-07-06
I don't have too much experience with this but here's the basics of compiling...

First throw your install CD into your disk drive (some files are on it which you'll need), open up the terminal (Appplications-->Accessories-->Terminal) and type the following:

```
sudo apt-get install build-essential
```

This will load the tools needed for compiling.

Next, using terminal again, navigate to where archive file is located (assuming you have an archive file) *.tbz or *.tgz?:

```
cd directoryname
```
 
where directoryname is the name of the directory you want to move into.

Once you're in the appropriate directory type:

```
tar zxvf FILENMAE
```

where FILENAME is the archive file..this command unpacks the archive...

Next type:

```
./configure
```

Then:

```
make
```

After that, type:

```
sudo make install
```

That *should* install the program...

That's about as far as I can help you...Good Luck!!

---

### Post by woedend on 2006-07-06
what makes you think its a driver issue?  what kind of card is it?  i dont see how it could be driver related if the livecd works.

---

### Post by professor_chaos on 2006-07-06
This kind of thing is happening to several people and it happened to my upgraded breezy->dapper on my hp laptop. 

If you open a terminal window and type ```
ping www.red.com
``` and you get hits, then its probably something wrong with your DNS. Although, I'm not entirely sure why it worked from the livecd.

---

### Post by woedend on 2006-07-07
you want to ping an ip address to test DNS.
try this
ping -c 5 4.2.2.1

try pinging your router/modem also.

---

### Post by Phosphoric on 2006-07-07
I've got exactly the same problem and it's been driving me nuts for a couple of weeks.  There are loads of threads about this and nobody has come up with a solution that suits everybody. :-? 

The best I can do so far to get internet access is this: (I'm at work on a Windows PC so bear with me) I go in to properties of eth0 and change from DHCP to Static IP.  Stick in my routers IP and gateway.  Click OK, try the internet...dosen't work.  Go back in to properties, change back to DHCP click OK and Voila!  Internet access is back again.  Trouble is, on re-boot, I have to do it again.

There must be a clue there to some of you clever people out there.  Please advise. :) 

Thanks people.

---

### Post by syedn on 2006-07-07
i'm a complete noob to linux in general too but i know for myself.. i had a livecd that worked once, but then when i did a real install, my internet connection didn't get picked up.  turned out that it (for me anyways) was because my broadband connection is PPPoE, it required some different configuring to get it working properly.  is that a possible option?

---

### Post by woedend on 2006-07-07
im certainly willing to help, but its very difficult because
a) each configuration is different
b) its much easier to do one on one, but naturally if your internet is out it becomes a chore.

---

### Post by Phosphoric on 2006-07-08
> **Phosphoric said:**
> I've got exactly the same problem and it's been driving me nuts for a couple of weeks.  There are loads of threads about this and nobody has come up with a solution that suits everybody. :-? 

The best I can do so far to get internet access is this: (I'm at work on a Windows PC so bear with me) I go in to properties of eth0 and change from DHCP to Static IP.  Stick in my routers IP and gateway.  Click OK, try the internet...dosen't work.  Go back in to properties, change back to DHCP click OK and Voila!  Internet access is back again.  Trouble is, on re-boot, I have to do it again.

There must be a clue there to some of you clever people out there.  Please advise. :) 

Thanks people.

Anyone? :(

---

### Post by Apple 101 on 2006-07-08
What kind of LAN card is it?

---

### Post by cyberlite on 2006-07-08
Ok so I had the same problem today, I installed the OS and try to connect to the net and nothing:confused:, being a complete noob at this and coming from win xp I read and read through alot of threads and nothing finaly I gave up. I tried to ping nothing, I saw that the network card was active, and still nothing after half a day gone by I did somthing I do same time to help computers renew the ip address I pluged it out waited a second and vuala it worked for a seconde or two I,m at a loss. ](*,)

---

### Post by Phosphoric on 2006-07-08
> **Apple 101 said:**
> What kind of LAN card is it?

It's built in to the MBoard and shows up in Win XP as NVidea.

Thanks.:)

---

### Post by cyberlite on 2006-07-08
So here is what I have ( or not)on my duel boot machine. In xp I have connection to internet. In ubuntu not.....:confused: , my router see xp but not ubuntu, I tried giving a static ip and in the router also and the mac addess, still nothing. I do get internet after a reboot for a second or 2](*,) ](*,), I read that it might be the ipv6 you have to torn it off but how?, I have seen many threads but nothing..................

---

### Post by Phosphoric on 2006-07-09
Bump....:(

---

### Post by cyberlite on 2006-07-09
Well good news after yesterday almost the hole day trying to fix the same prob as you have, I finaly try google, here is what I came up with it looks like that the most resent ubuntu does not like certen network cards like the one I had a [COLOR="Red"]DAVICOM[/COLOR],after the hole day trying here, and I tried it all with help from the guys, thx all, it toke my 2 min to install a card from realtek and vuala it worked no prob,( by the way there was nothing wrong with the davicom card I have a duel boot machine and it work under win xp), so for me, after one day shoot, I have it working. [-( I will see what I come up with for you, I'm also new here yesterday I installed my first linux so far so good, Its working good with xp.:rolleyes:

---

### Post by tommcd on 2006-07-09
If you dual boot windows and ubuntu and have an nvidia chipset see this:
[http://ubuntuforums.org/showthread.php?t=186848&highlight=nvidia+ethernet+unplug](http://ubuntuforums.org/showthread.php?t=186848&highlight=nvidia+ethernet+unplug)

Just a guess, but try shutting down, unplug the computer from the outlet for a bit, plug back in and boot Ubuntu. If you can now connect to the net, this is your problem.
Please report back if this works!

---

### Post by Phosphoric on 2006-07-09
That's funny, I repiled about 10 minutes ago and it hasn't shown up.:confused: 

Anyway, thanks for the link tommcd, a very interesting read.

I tried the power off trick for about 5 minutes but it did not work for me.:( 

However, what does work for me is to go in to the properties of eth0 via system/administration/networking and select a fixed IP, I put in my router's address.  Click OK and exit, still dosen't work.  Go back in and reselect DHCP and I'm connected for the rest of my session.  Unfortunately, on reboot I have to do it again.

Now there must be a clue in there for the networking gurus to work on, hope somebody can.

Thanks :D

---

### Post by cyberlite on 2006-07-09
When you say fix do you mean static?And when you bootup the static ip is gone?

---

### Post by Phosphoric on 2006-07-09
Re-selecting DHCP fixes the problem, but on reboot I have to go through the same sequence again ie select static IP click OK dosen't work, re-select DHCP, click OK now works for the rest of the session.

Another clue forgot to mention.  When installing the OS ( alternate version) it accesses umteen megabytes of programmes from the repositories or wherever, not off the disc, so there can't be anything fundamentally wrong with my hardware.

Thanks.

---

### Post by Apple 101 on 2006-07-09
Sorry, I thought I replied yesterday...

In a terminal: *lspci*.  Check the output for your nVidia card.  In a terminal: *lsmod*.  Check for the *forcedeth* module.  If it is not there, type in a terminal: *sudo modprobe forcedeth*.

---

### Post by Phosphoric on 2006-07-10
> **Apple 101 said:**
> Sorry, I thought I replied yesterday...

In a terminal: *lspci*.  Check the output for your nVidia card.  In a terminal: *lsmod*.  Check for the *forcedeth* module.  If it is not there, type in a terminal: *sudo modprobe forcedeth*.

lspci gives nVidia Corporation CK804 EThernet Controller (rev a3)

lsmod has a line forcedeth 23428 used by 0

Thanks

---

### Post by Apple 101 on 2006-07-11
In a terminal: *sudo insmod forcedeth*
[I]sudo ifdown eth0
sudo ifup eth0[/I]
Where eth0 is your nVidia card.

---

### Post by Phosphoric on 2006-07-11
oem@ubuntu:~$ sudo insmod forcedeth
Password:
insmod: can't read 'forcedeth': No such file or directory
oem@ubuntu:~$


Hmmmm.  forcedeth is definitely there when I run lsmod.

Can I find out where it resides and force the address?

Thanks.

---

### Post by Phosphoric on 2006-07-13
Well,  I've had this problem for over 3 weeks and still not getting anywhere.

Thanks to the people that have tried to help.

Guess I'm back to Microsoft.:(

---

