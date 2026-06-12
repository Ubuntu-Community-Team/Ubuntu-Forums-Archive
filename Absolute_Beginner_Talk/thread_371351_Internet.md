---
title: "Internet"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by icyblue on 2007-02-26
Hi,

In firefox, Only google page is displayed. When I enter the other site address, It says connecting to that site but finally, I got the error 'Problem loading page'. In google, search can be done but I can't proceed after that, same thing continues....So, Only one page is displayed but not others. Do you think somethin is wrong?
 
My internet connection is fine coz I'm using the same for Xp.

---

### Post by Dr Small on 2007-02-26
Try installing Konqueror or Opera and see if the problem persists.
If it doesn't, then it would mean there is a problem with Firefox, which you could reinstall.
What Version of Firefox are you currently running?

Dr Small

---

### Post by PartickThistle on 2007-02-26
Make sure your /etc/resolv.conf has your DNS servers in it.

It should be similar to
```
nameserver xxx.xxx.xxx.xxx
nameserver xxx.xxx.xxx.xxx
```
Where xxx.xxx.xxx.xxx is the IP address of your dns server.

Try going to [http://82.211.81.186/](http://82.211.81.186/) (UbuntuForums.org) and [http://82.211.81.166/](http://82.211.81.166/) (UbuntuLinux.org).  If you can, it's a DNS problem.

---

### Post by icyblue on 2007-02-27
Yeah, I can go to those to sites but not to any other site.... May I know, what should I do now?

---

### Post by chewearn on 2007-02-27
Open a terminal, type in this command:
```
sudo gedit /etc/resolv.conf
```

Type in your password, you should see a file with a line like this:
```
nameserver 192.168.1.1
```

The nameserver IP addresses should be your router's (if you have a router).  Else, you can find out the DNS IP address by using the same one as your Windows machine.

---

### Post by icyblue on 2007-02-27
yeah... I've the same thing as you've said in you last post...Can you tell me How to find that(IP address) in Windows?

---

### Post by chewearn on 2007-02-27
Open a command prompt window: Start -> Run -> cmd <enter>

Type in:
```
ipconfig/all
```

Find the line, which says "DNS Servers" of your active/LAN connection.

---

### Post by icyblue on 2007-02-27
ok... It says the same IP address '192.168.1.1'..... So, What's the problem then? Do you think it's basically due to an hardware(ethernet card) or is it due to ubuntu?

---

### Post by rjfioravanti on 2007-02-27
find an address that doesn't work in firefox, then try opening a terminal and pinging that address

so say [www.ubuntu.com](www.ubuntu.com) doesnt work in firefox

go to your terminal and do 

ping [www.ubuntu.com](www.ubuntu.com)


what happens?

---

### Post by chewearn on 2007-02-27
So, I assumed you didn't have the same problem in Windows; that is, you can surf to any site?

To be sure, how about if you ping some sites, e.g.:

```
ping www.google.com
ping www.ubuntu.com
ping www.yahoo.com
ping www.distrowatch.com
```

---

### Post by Ambimom on 2007-02-27
Try removing all your cookies and clear history and cache in Firefox Preferences/ Privacy......

Once you've done that....I'd reinstall and see if you can get back in...

Worth a try...

---

### Post by icyblue on 2007-02-27
When I tried 
'ping www.google.com'
'ping www.yahoo.com'
'ping www.ubuntu.com'

I got these lines repeated
64 bytes received from google(IP address of google)seq=1 ttl=45 time 267
These lines repeated with change in seq and time... It didn stop...
Same for all sites happened(same 64 bytes)....

I cleared all those cookies and everythin else and restarted it but I didn work

---

### Post by chewearn on 2007-02-27
This mean there is nothing wrong with your network connection and your DNS.  Ping is able to find all servers, but not Firefox.  Not being an expert on Firefox, I can only suggest you try reinstall in.

Go to Synaptic, select "remove completely"; that will make sure the Firefox configuration files are also deleted.  Then, install again.

Note: if you want to keep your bookmarks, make sure to export them first.

---

### Post by geezerone on 2007-02-27
Try looking under connection settings for anything which may be causing problems?

If you don't have the latest version of Firefox (2.0.0.2) try installing it from my link below.

---

### Post by icyblue on 2007-02-27
But I don't think it's due to firefox because in my Gaim IM, It's not connected( it means that it's says connectin but finally, couldn't connect raises). You have to watch this... In pinging the address... Server is identified but transfer of bytes goes on and on..... Like I said before, those 64bytes is received repeatedly for even 100times( I'm not patient enough to proceed. So, I closed the terminal).

Also, I can't use this 'sudo apt-get' because here,it's connectin to archive.ubuntu.com but It stops at 37%...

---

### Post by rjfioravanti on 2007-02-27
It is supposed to keep receiving those bytes over and over, it keep sending information to the address and then makes sure that it receives confirmation or whatever. So we have identified that you can resolve server names and send information to them, maybe you should try and figure out what is wrong with your apt-get before you worry about firefox

what happens when you do

sudo apt-get update

---

### Post by chewearn on 2007-02-27
That's just the normal behaviour for ping.  As long as it receive without error, there is no problem.  To stop ping, press ctrl^c.

---

### Post by icyblue on 2007-02-27
When I used the command ' sudo apt-get update'
Some 2 lines I got and then
37%[connectin t in.archive.ubuntu.com]. It stopped at this point....

Then, About the ping, Actually It goes infinitely... In windows, It stopped after receivin some 128 bytes.... but in ubuntu... It goes and never stops.... After some 300 times... It just changed it's site
64bytes from [www.google.com(........)](www.google.com(........))....
64bytes from bbc.co.uk(...)....

---

### Post by rjfioravanti on 2007-02-27
That is what ping is supposed to do, go indefinitely until you tell it to stop. Windows does it differently but that is ok.

Do you get an error at 37% or does it just hang? Sometimes it takes a long time to update your package listings if it is the first time you are doing it. What version of ubuntu are you running

---

### Post by icyblue on 2007-02-27
It just stops at 37%(I've to press ctrl+c)..... I'm usin ubuntu6.10....

---

### Post by rjfioravanti on 2007-02-27
please post the terminal output up to that point

and post the output to 

cat /etc/apt/sources.list

---

### Post by icyblue on 2007-02-27
Output of 'sudo apt-get update'
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/main Translation-en_US
Ign cdrom://Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025) edgy/restricted Translation-en_US
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy Release.gpg                              
  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release.gpg                       
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) edgy/main Translation-en_US                   
  Could not connect to in.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security/main Translation-en_US            
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
37% [Connecting to in.archive.ubuntu.com (1.0.0.0)] [Connecting to security.ubu


Then,
Are you sure about this command 'cat /etc/apt/sources.list'.... I jus got No such file or directory but sources.list is present in that particular loaction...

---

### Post by rjfioravanti on 2007-02-27
Well I want to see what is in your sources.list file

Mine is located in /etc/apt/sources.list, i think that is the standard location

Maybe you need to do 

sudo cat /etc/apt/sources.list

---

### Post by icyblue on 2007-02-27
Sources.list......

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by rjfioravanti on 2007-02-27
That looks fine

type ifconfig in your terminal and post that output

that command is similar to ipconfig in windows

---

### Post by Pedal_Pusher on 2007-02-27
I had a similar problem with Firefox.  I found the following info in a thread from mikeman ( #367498 ) which had been supplied by ubunutgoz :-

try disabling ipv6
a - in FIREFOX browser type about:config
b - in the Filter bar (just below address bar) type ipv6
c - in the next window down (preferences), you'll see a single line network.disable.Ipv6
, double click until it is bold and the value is true.

My Firefox now works fine but Synaptic and Update Manager are still useless - they timeout.

---

### Post by icyblue on 2007-02-28
this is the output of 'ifconfig'

eth0      Link encap:Ethernet  HWaddr 00:80:48:42:97:E2  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::280:48ff:fe42:97e2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7 errors:0 dropped:0 overruns:0 frame:0
          TX packets:33 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1598 (1.5 KiB)  TX bytes:4461 (4.3 KiB)
          Interrupt:177 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

---

### Post by icyblue on 2007-02-28
I did as said by pedal_pusher. Now, My firefox works but only firefox.... I disabled ipv6.. So what to do for other things?

---

### Post by rjfioravanti on 2007-02-28
Ok well I am not sure what is happening, though I will be interested in hearing the solution if someone else figures it out

You can ping addresses successfully so your internet is working

but you can't do updates because it can't connect to any of the ubuntu repositores =\

the only thing I can recommend is don't worry about firefox until you can do

sudo apt-get update
sudo apt-get upgrade

maybe getting that to work will fix firefox at the same time

it would also be interesting to know if you can download files from the internet using

wget <url>

---

### Post by icyblue on 2007-02-28
No....when I used wget<url> Same thing happens.... Only connectin to <url> and stops after that...
Do you think disablin ipv6 fully can solve the problem?

---

### Post by rjfioravanti on 2007-02-28
I did a bit of looking around on ipv6

It looks like it has caused many people problems

here are instructions on how to disable it

[http://www.ubuntuforums.org/archive/index.php/t-6841.html](http://www.ubuntuforums.org/archive/index.php/t-6841.html)

---

