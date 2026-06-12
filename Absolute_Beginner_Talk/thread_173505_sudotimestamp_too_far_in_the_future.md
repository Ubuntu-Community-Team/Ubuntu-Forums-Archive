---
title: "sudo:timestamp too far in the future"
date: 2006-05-10
forum: Absolute Beginner Talk
---

### Post by widyawan on 2006-05-10
Dear all,

When I try to use sudo command, I got a message "sudo:timestamp too far in the future". I get this message after adjust date&time from XWindows panel.
I can not use sudo since then. I already reboot but still the error appear.
Any clue how to fix it?
Thanks b'fore

Widy

---

### Post by johnc4510 on 2006-05-10
Open the adjust time and date again,
1.make sure it's set to 2006
2.Use the bottom tab to syncronize one time only with web.
Don't know if this will work, but a good place to start

---

### Post by RavenOfOdin on 2006-05-10
It worked for me.

---

### Post by widyawan on 2006-05-10
Unfortunatelly it's not work. I 've faced this problem twice. I think my first problem arose from different cause, but I can not remember how.

---

### Post by Mustard on 2006-05-10
Try this command..

```
sudo -K
```

Then see if sudo starts working again.

---

### Post by widyawan on 2006-05-11
After I restarted the computer it's work for me.
Could someone explain to me why this is happen and how to prevent this sudo:timestamp happen again?
Thanks ...

---

### Post by Mustard on 2006-05-11
I believe its a security measure to stop a method of getting around  certain security related restrictions by changing the date.  To stop people from changing the date to use this 'exploit', sudo gives this message if the timestamp is 'too far into the future'.  That's my vague explanation.  I've read about it in detail a long time ago, but I don't recall the exact details.  Basically if your clock is way out of sync and you change the date, this problem will occur.  There are methods of fixing it, but they are not well documented on the wiki or in the forum atm.  It might be an idea for someone to do the research and create a little HOW TO on how to resolve the issue. :)

---

### Post by rivimont on 2006-06-11
You should also be able to remove the user file in /var/run/sudo

I did this:
- su to root
- remove directory (rm -rf /var/run/sudo/username

Thats it.  Hope this helps.

---

### Post by Lil_Eagle on 2006-06-15
I never encountered this until today.  Unfortunately, it's impossible to su to root unless you already enabled the (by default disabled) root account.

To do that, you need to do sudo passwd, which of course you can't because it won't let you do sudo commands.

It is really annoying.  I think this issue changed my opinion of the sudo vs. su debate that is continuing.  I was editing my dchp settings, accidently forgot a semi-colon and now I can't change it!

I know I can reboot into the recovery console and fix it, but what is the point of having a stable system that doesn't need rebooting if you have to reboot it to fix a stupid error like this one.  It has to be a bug.

One thing I will certainly do is enable the root account.

There is another point to this sudo vs. root that people do not take into consideration.  People around you can see what passwords you type and if you have to type your own password to do administrative functions, then the chances are higher that others (family members for instance) will learn your password.

They have more opportunities to see you type it if you log in every time with the same password as you use for administrative tasks.  Alas, because almost all of the functions are coded to work with sudo, even after enabling the root account you still have to type the sudoer's password to access funtions, unless of course your in a terminal.

---

### Post by wizkrz on 2006-06-16
I was able to get around this by doing the following:

1. Check the timestamp sudo reports (will look something like below).
sudo: timestamp too far in the future: Jun 17 08:17:55 2006

2. Use Adjust Date & Time to set the date/time to the sudo timestamp or later.

3. Execute the 'sudo -k' command. (Clears the timestamp).

4. Use Adjust Date & Time to set the date/time back to the correct values.

Worked for me!

peace!

---

### Post by mjsoccer1 on 2006-06-17
Ran into the same problem, it occured after rebooting after installing updates... I still had some updates to install (a new linux kernal) so I installed that and rebooted... seemed to fix the problem.  wizkrz's instructions should work fine above.  This error is kind of weird, I've never had it happen before on Breezy or Hoary... as Mustard suggested, maybe some sort of security precaution included in 6.06 to stop users from changing the date to install programs?

As far as setting up a su, I would recommend doing it.  All other distros use su (except for Debian???).  Unless you have no idea what you are doing, installing under su is a lot easier than having to type sudo every time you want to run a command; its especially useful when compiling programs. Just my $.02.

---

### Post by cwc on 2006-07-02
I've run into this problem a couple of times. Most recently, I had performed a few administrative tasks, and then changed the system time via the date command. Shortly afterwards, I got the timestamp error message.

The solution (for me at least) was the command 'sudo -v'. The -k and -K options would not work, giving the very same timestamp error. So I glanced at the man pages. The -v option prompts for your password, and then resets your sudo timestamp as if you had just issued a normal sudo command (meaning you won't need to enter your password for another 15 minutes).

Anyway, that's how I fixed it. Hope this works for anyone else with this problem.

---

### Post by jayk123 on 2006-07-10
It is very easy to get into this situation by accident.
It is somehow related to timezone, like, some parts of the system using UTC, other parts using timezone-adjusted time. Could be related to using non-PC hardware that maintains hardwar time in UTC? I'm using a PPC iBook and have hit the problem repeatedly. I will try sudo -K, thanks.

---

### Post by Fyre2012 on 2006-07-10
Had the same problem...

solution was as wizkrz posted in my case...

Just had tp set the system clock in the future after the timestamp, sudo -K  , set the clock back to normal (or synchronize) and you're done

funny little one...

Thanks for the help

---

### Post by yohannmartineau on 2006-08-03
Hello,

I have the same problem with an ubuntu server version 6.06

The problem is that I cannot configure the time from any graphical configuration panel.

Apparently, a reboot is not enough because sudo keeps its timestamps in a file...

I made a mistake at installation I took GMT time but I'm in France it normally corresponds to GMT + 2... and now I cannot change time...

I will wait for the two hours that separated me from the sudo timestamp, but I really think this is a serious issue.

I am not an adept of sudo... I will probably activate su as soon as my sudo will come back... I think it's a pity ubuntu uses sudo. It distinguishes this distribution from others and is contrary to standards for users (even if they are administrators).

---

### Post by FiReWiRe1101 on 2006-08-25
> "I was able to get around this by doing the following:

1. Check the timestamp sudo reports (will look something like below).
sudo: timestamp too far in the future: Jun 17 08:17:55 2006

2. Use Adjust Date & Time to set the date/time to the sudo timestamp or later.

3. Execute the 'sudo -k' command. (Clears the timestamp).

4. Use Adjust Date & Time to set the date/time back to the correct values.

Worked for me!

peace!
Reply With Quote"

I can confirm this fix.

---

### Post by starscalling on 2006-09-10
> **FiReWiRe1101 said:**
> I can confirm this fix.

ditto!

---

### Post by mr. quippy on 2006-09-20
Confirmed once again. Motion passed. Problem solved ;)

---

### Post by ponsfrilus on 2006-09-20
damned! I have this problem on a server install (in a virtual machine in vmware)... The only way I know to change the date is:
```
sudo date -s "Wed Sep 20 16:08:00 2006"
```
and my sudo says "sudo: timestamp too far in the future"

Is that conencted to the type of date UTC, etc.? How can I change this on a server install? Is there a way to reconfigure the date without UTC?

Hopefully I know that if I reset my virtual machine the sudo cmd will work again!

---

### Post by ponsfrilus on 2006-09-20
First of all I think that my BIOS clock is set to UTC and not on LOCAL CLOCK but I don't know how to change it in the vmware but:
By editing this file **/etc/default/rcS** it's possible to set **UTC=no**
```
$ sudo pico /etc/default/rcS
```**change UTC=yes in UTC=no** in ligne 13

The command date give you the current time. If it's not correct set it with:
```
$ sudo date -s "Wed Sep 20 16:08:00 2006"
```

To change your timezone type:
```
$ sudo tzconfig
```

Reboot. All it's ok now. :)

---

### Post by winter.is.cool on 2006-09-22
I just had the same problem with a fresh install of Ubuntu 6.06.1 server.  I had just installed, made a few changes to /etc/network/interfaces and /etc/resolv.conf. The problem started I think after a reboot.

To fix the problem I booted into recovery mode (pressing Esc at the GRUB screen) and performed a sudo -k, then rebooted again normally.  So far the sudo command seems to be working properly again.

Thanks to those who gave the sudo -k tip!

---

### Post by domih on 2006-10-01
Got the same problem on an old G3. In my case the issue was the time difference between local time and GMT. Workaround: rm -fr /var/run/sudo as root.

---

### Post by Ptero-4 on 2006-10-03
The problem here is that in some machine (specially PPC Macs) Dapper doesn't add the genrtc module to /etc/modules and there is a missing rtc node in the udev list and a misplaced initscript regarding hwclock. There is athread about how to fix that. This have been fixed in edgy.

---

### Post by dubrict on 2006-10-13
I have this problem, and none of this works for me.  You cannot adjust the time without being the super user!  when I click "adjust date and time" it gives me the warning "su returned an error."  If I type "sudo anything" in the terminal, it gives me the warning about the timestamp.  This happened when I noticed my date was set 2 days ahead of what it is, and I changed it.  I don't mean to sound like a hothead but it's really ticking me off.

For me, the entire sudo or super user interface is pointless.  I'm the only person who has access to my computer.

---

### Post by arcticblue on 2006-10-21
I was having the same problem as the rest of you and nothing I tried on here would work.  What I did to fix it is run the "time-admin" command.  It came up with a gui and prompted for my password (right-clicking on the time and clicking adjust wouldn't ask for my password and would never open) and then allowed me to change the time.  I set the date and time to "the future" and then ran "sudo -k".  I was able to set the time back after than and now my system is fine.

So, to recap:
1.  Run "time-admin"
2.  Set the date and time to some time past the sudo timestamp
3.  Run "sudo -k"
4.  Change your time back using whatever program you want.

Hope this helps someone out.

---

### Post by ambient_sky on 2006-10-30
Hello all!
On Edgy Eft, the sudo -K helps me.
Its a solution.8)

---

### Post by 13ojo on 2006-11-15
i dont see how it works?.

it doesnt work for me, as i cant sudo and change the time..

---

### Post by reversial on 2006-11-19
Mustard, your method worked perfectly :). Didn't have to reboot, adjust my date/time zone, or anything. Thanks.

---

### Post by bodhi.zazen on 2006-11-28
> **reversial said:**
> Mustard, your method worked perfectly :). Didn't have to reboot, adjust my date/time zone, or anything. Thanks.

Hmmm....

I do not understand all this time stuff :p

Just when I think I know what is going on, it all falls like a house of cards :(

After a fresh Ubuntu install the date/time is always off even though I select the correct time zone.

I do not have windows on my box and I thought I was set to UTC....

At any rate, to correct the time I run:[sudo nptdate ntp.nasa.gov[/code]

This corrects the date....

This time I also ran into the "sudo:timestamp too far in the future" .....

Well, I could not do much since I had not yet set the root PW and now could not sudo....

Re-booting takes care of everything. Date/time is correct and I can sudo.

Yet still I do not understand why the date is of on a fresh install, why the timestamp error, and why rebooting fixes the problem.

HTH someone...

Thank you all for this interesting thread.....

---

### Post by Diiba on 2006-12-07
I found out a really easy way to use sudo, with the timestamp error.
Use command "sudo bash" in the xfce "Run program" app. (xfrun4), check the "run in terminal dialog" for some unknown reason it passes the time bug and gives lets you use the command with root account, so you can make all the wanted changes.
Worked for me.
For me the timebug was coused propably becouse of busted hardware battery (or something like that)

---

### Post by dwj on 2006-12-13
After a fresh install of kubuntu 6.10, the first time I logged in to my default user account and tried to sudo something, I got the timestamp problem. There is something puzzling about this, since many of the posts here recommend doing an operation that requires a sudo to do, which you can't do if the timestamp error keeps popping up. One thing I learned after a little playing around is that if you use one of the text logins (ctrl-alt-F2), you can login and the timestamp problem won't appear when you do a sudo operation. I have no idea why this is so, but it was for me. One of the posts had mentioned looking at the /var/run/sudo/user folder for the file(s) causing the timestamp problem. Sure enough, if your defaul user is adam, there will be some files like /var/run/sudo/adam/1 (or 2 or 3, etc) that have a timestamp in the future. Just type the following command from the text login:

sudo rm -f /var/run/sudo/adam/?

Use ctrl-alt-F7 to get back to your GUI logon. Logout and when you log back in again, the problem should be solved.

---

### Post by Yuma on 2006-12-14
Hi there,

I don't know how did you do to change the Time/Date without sudo, but at least in my case I can't do it. I don't even look what's inside /var/run/sudo so no talking about deleting something. But for some strange reason the last post of **dwj** give the solution in my case.

I don't what you think, but this can't happen. Haha, I mean, no matter if it's a super server or the personal computer of a gamer, but I feel like this a an important bug like somebody told already. Someone knows why happens this? I've read that it may be caused by a battery switch, thing I did this evening, so maybe the bus is that way.

I'll do something, unplug the computer and wait for... let me see... 20 minutes? And then report what happened. If someone knows why may be cause, please tell something.

Cheers!
Alejandro Cámara Iglesias

---

### Post by Yuma on 2006-12-14
Hi again,

It seems nothing happened... Well, it was worth the try. More ideas?

Alejandro Cámara Iglesias.

---

### Post by Lexicon11 on 2007-01-25
I am found an interesting workaround! I deliberately changed the time and noticed that "sudo -K/k" does not work. Usually timestamps are cleared within 15 minutes, but sometimes it does not work. 

The workaround is to start another session without logging out of the current session, and you can log in with the username/password as ubuntu allows you to log in multiple sessions. Then you could change the time and date as it was in the original "sudo: timestamp..." error or past that date and then end that session. Voila! the date is changed in your original session and sudo works perfect!!! :guitar:  

You're welcome!!!

---

### Post by ashmew2 on 2007-01-27
well i was facing the same problem and im using Dapper Drake 6.06 and in the terminal no sudo commands were working with the error "timestamp too far in future".SO what i did was that i opened another terminal (keeping the first one still open) and in the new one typed "sudo -K". This fixed the problem in both terminals and overall :D LOL. Hope this elps u too :)

---

### Post by mrfelker on 2007-02-04
Another thing.  If you have installed ntp and sync to Internet servers you will get this absurd error.
Just remove ntp (5 programs) using synaptic and it disappers.:)

---

### Post by s26c.sayan on 2007-02-07
> I was able to get around this by doing the following:

1. Check the timestamp sudo reports (will look something like below).
sudo: timestamp too far in the future: Jun 17 08:17:55 2006

2. Use Adjust Date & Time to set the date/time to the sudo timestamp or later.

3. Execute the 'sudo -k' command. (Clears the timestamp).

4. Use Adjust Date & Time to set the date/time back to the correct values.I confirm this fix too!!!! :)


I love my Ubuntu...but these sudden hitches really irks me!! :( (Though it'l take more than a few of such 'bugs' to convert me away from ubuntu!! ;))

---

### Post by dupa on 2007-02-07
you can reboot the machine, and choose in the grub menu the "recovery mode" options, so you will be logged as root and you can do any change to system.

however i had the same problem when i updated the system date with ntpdate, it set the date to a previous date, and sudo get angry for some reasons..

---

### Post by spartawizzard on 2007-04-10
if  "sudo" doesn't work and you cannot use "adjust time for any cause" try this  way:

1- go to: System-administration- User & groups. Select "root", then Proprierties, set the password for root(i set the same i have for my user), go to "user priviliges" and enable all box.
ok and close

2- open terminal window and run this command:
  $ su
  password: (the password you set the step before)
Now you are in root mode.

3- change the time later than the timestamp
4- run the command "exit"
5- run the command "sudo -k"
6- repeat step 2 and then set the right time
7- now you can run the command sudo without any error

---

### Post by MichaelSammels on 2007-04-12
I would use the above option, it seems to work for everybody. Thanks all!

---

### Post by the red krawler on 2007-04-23
> **rivimont said:**
> You should also be able to remove the user file in /var/run/sudo

I did this:
- su to root
- remove directory (rm -rf /var/run/sudo/username

Thats it.  Hope this helps.

G'day all.

I just struck this problem myself, and this is the only solution that worked for me. Just to make it even more simple, it went down like this:

```

username@file-server:~$ sudo ls
sudo: timestamp too far in the future: Apr 23 17:19:43 2023
username@file-server:~$ su
Password: 
root@file-server:/home/username# rm -rf /var/run/sudo/username
root@file-server:/home/username# exit
username@file-server:~$ sudo ntpdate ntp.nasa.gov
23 Apr 17:24:55 ntpdate[1064]: adjust time server 198.123.30.132 offset 0.020390 sec
username@file-server:~$ sudo ls
nothingtoseehere.txt
username@file-server:~$

```

Hope this helps someone else. I spent a bit of time trying the various -k, -K, -v options suggested, but nothing worked for me. Perhaps since I've got no GUI and the other solutions rely on multiple console windows? Either way, this worked and no rebooting (dont want to ruin the 115 day uptime over a stupid time issue!)

Regards.

---

### Post by hardwarehank on 2007-04-27
I used gksudo to fix it.  Apparently they use different temp files.


```
hank@rura-penthe ~ $ gksudo "sudo -K"
hank@rura-penthe ~ $ sudo ls
ArtistsToInvestigate                  no
#....
```

---

### Post by crafter on 2007-07-04
I had a similar problem,a dn none of the solutions worked for me...

...until...

I started a new terminal (Ctl-Alt_F1) and run 'sudo -k'

I discovered that you current sessions seems to be locked. For example, opening a NEW terminal window in gnome-terminal will accept the 'sudo -k' command, while your current  sessions will give the timstamp error.

Hope this helps someone.

---

### Post by smoka on 2007-09-19
As I had installed 7.04 server in VMware and not enabled root login, evetually found the following worked:

sudo -i
sudo -k
exit

now I can sudo normally again :)

---

### Post by MageMasher on 2007-09-25
> **Diiba said:**
> I found out a really easy way to use sudo, with the timestamp error.
Use command "sudo bash" in the xfce "Run program" app. (xfrun4), check the "run in terminal dialog" for some unknown reason it passes the time bug and gives lets you use the command with root account, so you can make all the wanted changes.
Worked for me.
For me the timebug was coused propably becouse of busted hardware battery (or something like that)
I run kde and couldn't do the "ajust time & date" trick as its a gnome program. I was able to do what Diiba using the kde run dialog, that gave me a konsole asking for my password which then gave me root access and allowed me to "rm -rf /var/run/sudo" giving me back sudo :D

---

### Post by cyberwiz on 2008-02-06
I used (from the root terminal) **touch /var/run/sudo/[username]/[all files in this directory].** 

The sudo complains if the timestamp on any of these files lies too far ahead in the future,

---

### Post by balexand on 2008-03-20
I was able to get root access using gksu even though sudo wasn't working:

gksu gnome-terminal
sudo -k
sudo -K

---

### Post by thinkerisme on 2008-03-24
> **wizkrz said:**
> I was able to get around this by doing the following:

1. Check the timestamp sudo reports (will look something like below).
sudo: timestamp too far in the future: Jun 17 08:17:55 2006

2. Use Adjust Date & Time to set the date/time to the sudo timestamp or later.

3. Execute the 'sudo -k' command. (Clears the timestamp).

4. Use Adjust Date & Time to set the date/time back to the correct values.

Worked for me!

peace!

This the correct way to solve this problem!

---

### Post by alowe on 2008-03-31
run:
sudo sudo -k
this will ask you for your password again, and kill the timestamp of the original sudo.

This worked for me.

---

### Post by dom on 2008-04-28
> **Mustard said:**
> Try this command..

```
sudo -K
```

Then see if sudo starts working again.

Cheers Mustard,
This sorted it out for me.

Just installed Ubuntu 8.04, Hardy Heron, and noticed that it was 1 hour ahead at boot, then I can do very little after login due this clock issue.

Using sudo on it's own with '-K' seems to have fixed up the issue and other sudo commands now work again :)

---

### Post by -random on 2008-06-13
> **dom said:**
> Cheers Mustard,
This sorted it out for me.

Just installed Ubuntu 8.04, Hardy Heron, and noticed that it was 1 hour ahead at boot, then I can do very little after login due this clock issue.

Using sudo on it's own with '-K' seems to have fixed up the issue and other sudo commands now work again :)

after reading the differences between '-K' and '-k' with ```
man sudo
``` i think it's better to use '-k' becauze you still keep the intedned functionality of the timestamp? (correct me if i'm wrong or got it the other way round plz!)

---

