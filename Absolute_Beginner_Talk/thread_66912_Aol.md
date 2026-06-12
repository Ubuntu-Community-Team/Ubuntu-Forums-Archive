---
title: "Aol"
date: 2005-09-18
forum: Absolute Beginner Talk
---

### Post by Warpnow on 2005-09-18
Okay, so I have never sat down in front of a linux machine. I have worked with them through shells as servers for about a year now and run several programs that I can't test locally, which annoys me as a windows user. I like Ubuntu from the live Cd and would like to switch, but I am on AOL dial-up and I am not sure if I could ever get Ubuntu to work on my pc, anyone know if its possible?


I know I should switch providers, but that's not what I am asking if you feel compelled to convert me to non aol.
 [-X  :razz:

---

### Post by wmcbrine on 2005-09-19
I've read that it's possible to connect to AOL dialup via SLIP (Serial Line IP, a kind of predecessor to PPP), with an appropriate script. I haven't tried this myself. I quote Roger Simpkins, from Usenet:

> This is an answer to an OLD thread here but will provide some insight. I ended up moving out of my DSL range and got "stuck" with AOL for a while.  I have found out how it works finally.

It turns out that they connect to the Sprint backbone and then initiate a CSLIP connection into their servers.  You can set up a DUN connection by using a script.  Call the local access number, this will be a sprint number. Enter AOL as the username and then a blank password. You will then be in the AOL network.  The you can initiate a CSLIP connection using your AOL username and password.

I am sucessfully sharing a AOL dialup connection on my network without their software and using Routing and Remote Access on my 2000 Server (this should also work on a XP box).

---

### Post by Warpnow on 2005-09-19
I found a dialer called PengAOL, but can't get it working right...anyone used it before?

---

### Post by ddemers on 2005-09-19
Not trying to flame, but in all honesty get a different service.  If you want to move to a Linux system AOL will offer you nothing that another service provider would off you.  

AOL internet is a very odd service, I have always had a service provider that just connected me to the Internet then I was able to do what I wanted to do online, probably why I never really understood why AOL was any good.

---

### Post by Z_Cee on 2005-11-10
In my area AOL is the best internet provider and I determined this after I tried several others. Net Zero, People PC, and Earth Link just to name a few. I get better speed with AOL and they've reduced my monthly bill as well. (DSL or Cable is not available in my area).

Does anybody know how to get Ubuntu to work with AOL?

---

### Post by whythehellcantilogon on 2005-11-14
I am new to this so if anything dosen't work right, let me know.

To get dial up aol to work: (I am assuming you have your modem working already)
Get the program called penggy. I don't remember where I got it but you should be able to find it with google. If you can't let me know and I will email it to you.

change to the directory you downloaded it to 

**sudo dpkg -i (nameofpenggyfile)**

You need to edit several files to let it know your screen name and password before you can use it. 

(I am at school right now so I am not sure if these are exactly right).

**sudo gedit /etc/penggy/penggy.cfg**       
  All I did was add my screen name and tell it where my modem was.
         screenname = guitarfool1999
         modemdevice = /dev/ttyS0  ???? (yours may be different)
**sudo gedit /etc/penggy/.aol-secrets**  ??? (not sure whether to include the ".")
         Enter your screen-name and password like the examples
**sudo gedit /etc/penggy/phonetab**
         You need to find out the number(s) you use to dial up, just enter it/them. I didn't need or know what any of the other options did so I just left them blank.

Then run the program with "sudo penggy" from the terminal. To quit just push ctrl+c in the same terminal.

ps- on one of my computers it dialed and went through the whole process and such but ended in an error saying it couldn't write to a certain file. If this happens just make the file
sudo gedit /place/and/name/of/file
and save the blank file

-When I get home I will edit this and make sure everything is right

Hope this works for you.

---

### Post by nitricacid on 2005-11-15
While we are on the subject of AOL...
I have in the past (5+ years ago to be exactly) used AOL (never with linux however) and was able to get my service for free for atleast 6months.

It all started when I got a CD in the mail and then when I called to cancel my subscription after the one month trial period, be for I knew it i had it for 6months.
----

I don't know how their policy is now days since the only reason i ever used AOL in the first place was because it came with a free month & I didn't have any other ISP at that time.

In my opinion spending $30 to surf the web at less then 56k is a big waste of money. I can get DSL for only $20 or CABLE for $40 (I understand the service may not be availible in all areas so don't go flaming me about this).

---

### Post by Z_Cee on 2005-11-15
Thank You whythehellcantilogon. When I get my test box going I'll surely do what you recommended.

nitricacid - I've gotten AOL free for 6 months at a time as well because of a new computer purchase. Then they discounted my monthly bill after then.

The only reason I use AOL is because I do not have access to cable or DSL in my area. AOL dial-up has the best speed in my area. I've thought about getting one of the small satellite dish for DSL, but they are several hundred dollars(US) and the service starts at $60 and all of that is way to much for me.

---

### Post by nitricacid on 2005-11-15
[QUOTE=Z_Cee]
nitricacid - I've gotten AOL free for 6 months at a time as well because of a new computer purchase. Then they discounted my monthly bill after then.
[/QUOTE]

No, you don't understand.
I got a CD in the mail, not from a new computer purchase.
Lets just say that if you bitch about your service enough they will give you a month free.

---

### Post by cuiq on 2005-11-15
Here are some instructions for PengoAOL

[http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html](http://www.yolinux.com/TUTORIALS/LinuxTutorialAOL.html)



Peace V

---

### Post by Z_Cee on 2005-11-16
Thank You!


...and YES -- God loves me!!

---

