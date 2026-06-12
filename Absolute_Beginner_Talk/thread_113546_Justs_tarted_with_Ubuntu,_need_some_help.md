---
title: "Justs tarted with Ubuntu, need some help"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by achafe on 2006-01-06
I've started setting up ubuntu on an old pc.  I am completely new to this and am looking for some help!!

I did a server instal...it went beautifully onto a partition, everything was great!

When I try to login as root (ie typing #sudo -s, sudo passwd root, etc..) I get the message:

sudo: unable to look up via gethostname()

Can anybody please tell what I'm doing wrong?
I tried searching the forums and google, but couldn't find much help, so I thought I'd post!

I also have no idea how I would go about setting up my linksys wusb11 v2.6 (Atmel) network adapter, if someone could point me in the direction of a step by step howto I would be their best friend!! :)

Thanks in advance everyone!!

---

### Post by Mathias-K on 2006-01-06
Hi, i'm quite new myself, but i don't think you are able to run as root in Ubuntu. You rather run as sudo when you need the priviledges, like "sudo kcontrol" if somethings wrong for me in Kubuntu :)

I'm afraid that's all i can help with for now.

---

### Post by achafe on 2006-01-06
Thanks for your help!

I found out that I can run as root by logging into grub in repair mode!

If someone could help me with my net. card I could get my system up and running!

I just tried ndiswrapper but it wouldn't work.  So I tried "apt-get install ndiswrapper" and it couldn't find the package.  Even with the Install cd in the drive and mounted.

Any ideas??

---

### Post by Jussi Kukkonen on 2006-01-06
Sounds like your computer does not find itself... What's in your */etc/hosts*?

It should have a line like:
```
127.0.0.1 localhost.localdomain localhost <yourhostname>
```

EDIT: crap, should have refreshed before writing...

---

### Post by nalmeth on 2006-01-06
I took a long road trying to install a usb wireless adapter. I hope you have direct internet connection for now anyway! Basically I tried ndiswrapper (a graphical frontend to it) and it didn't work. 
Ultimatly I found a company called linuxiant or something that covers all non-free drivers and charges you $20 for a lifetime membership, with 30-day free trial. I can't say this is your only option, but it's all I could find.

BTW

Ubuntu has no root user to begin with. Sudo is used for admin purposes. If you would like you could create a root user with full admin priveledges. Search the forums.

---

### Post by achafe on 2006-01-06
thanks for the tip!

i can't get ndiswrapper to run at all.  ie: I enter "ndiswrapper -i /path/to/driver.inf"
And get nothing but an error message and apt-get ndiswrapper reveals that package is not available!

I sure wish these wireless card where easier to work with ubuntu! :(

---

### Post by nalmeth on 2006-01-06
wait for dapper my friend!

but if you can't, you can spend 20 bucks, or find a way into tricking linuxiant into 3 free 30 day memberships! :p

EDIT: search for an ndiswrapper GUI. It may just work, and it is more user-friendly!

---

### Post by achafe on 2006-01-06
can I run ndiswrapper GUI without a desktop?

dapper?  more card support? sounds worth while! haha

I'll keep trying things and see if I get anywhere.

---

### Post by peanut butter on 2006-01-06
for yourproblem running as root: type 

sudo passwd root
<enter>
<your password>
<enter>
<What you want the root password to be>
<enter>
<What you want the root password to be again>
<enter>

this will allow you to use su and login as root (this is not a good idea)

---

### Post by achafe on 2006-01-07
OKay, now when I type:

"sudo passwd root"  

it gives "sudo: unable to look up via gethostname()"

But If I boot into recovery mode I have root privleges anyway, so it doesn't seem like a big deal.

---

### Post by Mustard on 2006-01-07
The answer is in the post above, from Jussi Kukkonen, regarding your /etc/hosts file.  You need to log in as root and edit that file.  Using recovery mode from the grub menu should get you there.  Adding a hostname to the /etc/hosts file should fix the problem.  If you have any questions on this process just ask.

---

### Post by jesrah on 2006-01-07
hello all novice in linux can't even get the live cd to work sticking at "enter presession........" 2 hrs and nothing stuck on 10% configuring snapshot
need help please

---

### Post by Crochetchick on 2006-01-07
> Adding a hostname to the /etc/hosts file should fix the problem. If you have any questions on this process just ask.

Mustard! You are my savior! I am having this problem and not able to do anything except surf the web and the Open Office Program.

Please can you give me step by step directions how to add my name to the hosts file!?

Thank you for helping!

---

### Post by donkle on 2006-01-07
[QUOTE=Mathias-K]Hi, i'm quite new myself, but i don't think you are able to run as root in Ubuntu. You rather run as sudo when you need the priviledges, like "sudo kcontrol" if somethings wrong for me in Kubuntu :)

I'm afraid that's all i can help with for now.[/QUOTE]


If you type 'sudo -s -H'  without the quotes in the terminal and enter your password when asked for it you wil remain root as long as you stay in the terminal.  You can even change terminals if you don't let more than five minutes pass.

---

### Post by Mustard on 2006-01-07
[QUOTE=Crochetchick]Mustard! You are my savior! I am having this problem and not able to do anything except surf the web and the Open Office Program.

Please can you give me step by step directions how to add my name to the hosts file!?

Thank you for helping![/QUOTE]

Ok..well I am assuming you are getting the same error message "unable to look up %name via gethostname ()" when using the sudo command, so with that in mind I'll try my best to explain the process in detail.

Since sudo is not functioning, editing the system file /etc/hosts is not possible using the sudo function, so it is necessary to gain a 'root prompt', that is a command line prompt where you are logged in as root.  The easiest way to do this is to use the recovery mode option in your grub boot menu when you start up your computer.  This should allow you to drop to a root prompt in command line mode.  This link below explains this process and other methods of doing it too.

[http://www.ubuntuguide.org/#gainrootwithoutlogin](http://www.ubuntuguide.org/#gainrootwithoutlogin)

Recovery mode through the grub menu is the easiest though, so try to stick to that method and only use the others if you have problems getting a root prompt through recovery mode.

Once you have gained a root prompt, it is necessary to edit the file called 'hosts' which is contained in the etc directory. To do this you would use an editor that works in terminal, like nano (for gnome), or kate (for those using KDE).  Assuming you are using gnome, you would type this command to open up the /etc/hosts file..

```
nano /etc/hosts
```

Your /etc/hosts file will look something like this below, but missing the part at the end where mine says 'slave'.  That is what I called my computer when I first installed ubuntu.  By default the install setup usually calls the computer 'ubuntu'.  What you need to do is to add your hostname to the end of the first line with a hostname that you want to call your computer.  You can call it whatever you like.  My choice was to call it 'slave' obviously. :)

```
127.0.0.1       localhost.localdomain   localhost       slave

# The following lines are desirable for IPv6 capable hosts
::1     ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

```

You can use the 'hostname' command to see what your current hostname is.  Just type this in terminal..

```
hostname  #this command will return your current hostname

#to change your hostname you can do this below

hostname yourhostname  #substituting your chosen hostname for 'yourhostname' will set your hostname
```

References for the above commands can be found by using the 'man' command, which opens manuals for the various commands.  A common question is 'How do I exit the manual', so I'll get that out of the way now.  You hit the 'q' key to get out of a manual in the command line.

```
man nano  #manual for the command line text editor
man hostname  #manual for the hostname command, also contains some information on /etc/hosts
```

I'm hoping this is enough information for you to be able to complete this process.  If I have missed something along the way, feel free to ask further questions.

---

### Post by achafe on 2006-01-10
Thanks guys, I have the sudo issue all cleared up!  Still can't get the wireless card to work...although I have one more thing left to try, if I need anything, I'll certainly ask you guys!

On another note, I did a full Unbuntu install on the family computer (different, new and fancy pc), and it runs beautifully!  such a great OS and sexy desktop!  No more winodws XP crap for me!

---

### Post by Mustard on 2006-01-10
[QUOTE=achafe]Thanks guys, I have the sudo issue all cleared up!  Still can't get the wireless card to work...although I have one more thing left to try, if I need anything, I'll certainly ask you guys!

On another note, I did a full Unbuntu install on the family computer (different, new and fancy pc), and it runs beautifully!  such a great OS and sexy desktop!  No more winodws XP crap for me![/QUOTE]

Congratulatons.  Well done. :)

---

### Post by Crochetchick on 2006-01-11
Thanks for taking the time to help us, Mustard.

---

### Post by patrick295767 on 2006-01-11
Server Install:
[http://www.ubuntuforums.org/showthread.php?t=64557&page=8](http://www.ubuntuforums.org/showthread.php?t=64557&page=8)

---

