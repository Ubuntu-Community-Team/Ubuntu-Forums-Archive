---
title: "Internet connection"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by Unclebill on 2006-09-21
So I am new to unbuntu.  I have installed it Ver. 5.10 and am excited to explore this new OS.  I am fairly computer freindly.  I own4 macs and 2 PCs.  I installed a seperate HD and load ubuntu on to that HD.  So far it is up and running except for my internet connection.  can't seem to find the fix.  I went to the documentation connected to this forum as well as a couple of books, looking for help.  In fact I am not 100% sure it is not working.  for example when I launch firefox I can access some other pages but they are all firefox related.  Additonally when launch update manager it recongnizes that there is an update.  i am willing to spend some time figuring this out but I am lost at present.  

PS i'm using a mac to post this question.
Thanks for the help in advance

---

### Post by Mark_in_Hollywood on 2006-09-21
Using one of your many computers or access through a public ISP (Starbuck's or Internet Cafe)

see:

[https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems](https://wiki.ubuntu.com/DialupModemHowto?action=show&redirect=SettingUpModems)

however, as you didn't say the type of connection/modem you have, responses must needs be limited.

I suggest if my foregoing isn't helpful to re-post with more specifics.

---

### Post by whizbaby on 2006-09-21
Try (in terminal)
ping [www.ubntuforums.org](www.ubntuforums.org)
to be shure that you have no connection.
If so, how do you connect to the internet (router,modem,wireless)?

---

### Post by Unclebill on 2006-09-21
Thanks for the quick replies.  I am connected via ethernet to a ethernet hub to a DSL modem  (Actiontec) via Qwest.   Computer is a custom PC built for my CNC/CAM drafting needs.  AMD3000+XP HD.  Both Eterhnet ports are detected by Ubuntu.  I pinged as sugessted and recieved some fairly encyrpted (at least to me) response.

Thanks
Bill

---

### Post by Unclebill on 2006-09-21
I believe my connection is functioning because this Mac that I am using to post is connected to said ethernet - ethernet hub- DSL modem- qwest etc.   Additionally if I reboot the PC I am running ubuntu on and let it boot up using windows it too can connect to the internet.  So I do not belive it is the "system" beyond ubuntu that is problematic.  At least not to other OS.   

Bes regards,
UncleBill

---

### Post by whizbaby on 2006-09-21
> **Unclebill said:**
>  recieved some fairly encyrpted (at least to me) response.
Bill
...and why not posting it ?...
(is there something like *time=64.8 ms* in your 'encrypted code'? This means your connection is up and you have to be a little more precise about the symptoms you experience.)

---

### Post by Unclebill on 2006-09-21
Nothing like "Time+64.8 ms"

---

### Post by whizbaby on 2006-09-21
so..(sigh)...can you copy-paste it and post it so one could see it?

---

### Post by Unclebill on 2006-09-21
Yeah so I know its a pain in the ****.  The reason I did not post the results of the ping is because the computer that I have Ubuntu installed on is not the same as the one I am using to post this message.  So to show you what the ping results are I must hand type the following
Usage: ping [ -LRUbfnqrvVaA] [-c count] [-i interval] [-w deadline]
                   [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
                   [-M mtu discovery hint] [-S sndbuf]
                   [ -T timestamp option] [ -Q tos] [hop1...] destination

So now that I have copied that I am not sure about spaces between all of this.  Some places looks like there is a space and I have copied that as I have interpeted it.  Do capitals make a difference??  I have tried to copy this exactly as I see it.
So what does "pinging" do?  when I ping am I sending out 
"packets" of information?  then can you (or I) get some info by what is returned to me?
This is the absolute beginners forum, yes??? 

Thanks again
Uncle bill

---

### Post by Unclebill on 2006-09-21
Ok so to continue with my ignorance.  When using the terminal and typing in commands what counts and what doesn't?  the letters in the correct order probably are essential. But what about capital letters vs. lowercase letters?  How about the formatting?  When I posted that last reply the resulting formatting is different then what I typed.  Does that matter?  What about fonts?  Any taboo fonts??  In "golden" or default Fonts"  What other criterea is there.  I am asking so as to help ensure success by paying attention to the correct details.


Best regards,
Uncle bill

---

### Post by podunk on 2006-09-21
Hey Uncle Bill,

first of all I'm a newbie to - so keep that in mind!

When you type "ping" you have to add the name of a website after command "ping" like this:

ping yahoo.com

and should get results that look like this:
64 bytes from w2.rc.vip.dcn.yahoo.com (216.109.112.135): icmp_seq=82 ttl=54 time=35.3 ms


it will continue to ping packets off of Yahoo.com until you type the keys
<CTRL> <C> (<cmd> <C> on a mac maybe?)

In answer to your other questions - linuix *is* case sensitive - Ping is not the same as ping. Spaces are important also.

You might want to look at this page for help:
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_broadband_connections](http://easylinux.info/wiki/Ubuntu_dapper#How_to_configure_broadband_connections)

I installed Ubuntu on Windows computers. Windows is very insecure (as we all know) and Ubuntu was able to get my connection info (PPP user name and password) from the windows files - this might not be possible on a mac. :-)

I don't have any font options in terminal mode?!? I click
Applications
Accessories
Terminal

to get the command module.

Wish I could help more!

---

### Post by whizbaby on 2006-09-21
The terminal is case-sensitive (lower-upper-case) because the filesystem is.
ping sends an echo_request (some network standard) to the adress you type
*ping [www.ubuntuforums.org](www.ubuntuforums.org)*
*ping 168.192.100.129* (some fantasy-IP-adress)
*ping fantasyhost* (example for ping *hostname*)
for a complete manual type *man ping*
What you saw is a brief summary of the usage of *ping* (did you type an adress? If network is not active and you try to ping a server in the internet it would say *unreachable*).

---

### Post by Unclebill on 2006-09-21
Alright!!!  It apears that when I ping yahoo.com received packets back.  Which I am assuming means I have internet connection.  So thanks for the help & I will continue on ward.

Best regards,
Uncle bill

---

