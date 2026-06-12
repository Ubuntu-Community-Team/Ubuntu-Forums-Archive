---
title: "Eye candy for 5.10"
date: 2007-03-08
forum: Absolute Beginner Talk
---

### Post by Drew555 on 2007-03-08
I've just managed to get 5.10 running on my PC, and have downloaded the 6.10 .iso.

I have to wait till I get new CD-Rs before I can install it (I believe) and want to 'pretty up' 5.10 while I am using it.

Normal desktop eye candy sort of stuff, like transparency and things like that.

Any one help?

Beware, I am a proper n00b (don't know what a 'repository' is, even after searching)..

Oh, and when I click on 'add/remove applications', my computer goes 'dong' and nothing happens.

Any ideas?

:EDIT: and I'm scared to install the updates (209 of em) because last time I did it I messed it up somehow and ended up having to reinstall :(

Please help a n00b...it's national help a n00b week after all....

---

### Post by STREETURCHINE on 2007-03-08
i think you will find you should be fine installing the updates,as you will need some of the packages that are in them..(i think so any way)

 then can you paste the out put of the command bellow just copy and paste it to terminal 

applications>accessories>terminal    

           ```
cat /etc/apt/sources.list
```

so you will have to update anyway.

---

### Post by AtrejuT on 2007-03-08
you should also be able to upgrade your system without having to burn any CDs, if you do have a fast internet connection.
To do that you should, however first install all the updates that are waiting. Then you have to upgrade to 6.06 by running 
```

sudo update-manager -c

```
(I think) in a terminal.

atreju

---

### Post by Drew555 on 2007-03-08
Right, I'll have a go at the 200-odd updates...

Can someone do me a step by step walkthrough, so I don't bugger it up again?

I really don't wanna be reinstalling again....

:edit: surely it can't be as simple as right click on the update icon (top right) and select install all updates?

Thats not very linuxy.

There's got to be more to it than that...

---

### Post by AtrejuT on 2007-03-08
Well, but it's very Ubuntu!
At least that's how I did it, and it always worked for me...
If you want to have slightly more control you could start synaptic (System/Administration/Synaptic in your menu) and then do 'Mark All Upgrades' and 'Apply'

Let me know if you run into problems.
Atreju

---

### Post by Drew555 on 2007-03-08
Bet you knew this was coming.....
Started the updates by clicking on install all updates, then clicked on the mark button...waited for the updates to download and install.

All good so far.

When it finished, this error popped up.


The following problems were found on your system:

E: python2.4-minimal: subprocess post-installation script returned error exit status 139


Is this a really bad thing?

Could it be caused by  the screensaver coming on during the install process?

Do I need to panic yet?




:edit: closed that error window and got this.....


Changes applied.

failed to apply all changes! Scroll in the terminal buffer to see what went wrong.



Whats the terminal buffer? and will I be able to do anything anyway?

---

### Post by AtrejuT on 2007-03-08
ok, I don't know why that happend but it doesn't sound too bad, it's just python...
Your system should still be running fine!
The first thing I'd try if I was you is do the 'reload' 'mark all upgrades' 'apply' thing again in synaptic. See what happens and let me know.

atreju

---

### Post by Drew555 on 2007-03-08
Will do my man,

Any ideas on something that works like beryl for The Badger?

---

### Post by AtrejuT on 2007-03-08
Well, as far as I can see Beryl only works from Dapper onwards:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)
I have no idea about compiz, which is the other option for fancy bling bling.
But as I mentioned somewhere you can upgrade to dapper without burning a CD (if you dare after this upgrade... ;-) ), and since dapper is the most stable version of ubuntu I'd consider doing that in any case.

Good Luck
Atreju

---

### Post by Drew555 on 2007-03-08
Thanks Atreju, you've been a diamond.

All updates successfully installed, add applications working and ubuntu running stably.

+kudos for you, my new best friend.

Now I've got it working properly, I'll cock it up by upgrading to Dapper.......

:edit: just tried that code you posted for the ugrade to 6.06

sudo update-manager -c

Gave me this...


drew@mission-control:~$ sudo update-manager -c
Password:
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
/usr/lib/python2.4/site-packages/UpdateManager/MetaRelease.py:171: DeprecationWarning: Class MetaRelease is already GObject-registered; Please note that classes containing any of the attributes __gtype_name__, __gproperties__, or __gsignals__ are now automatically registered.
  gobject.type_register(MetaRelease)
usage: update-manager [options]

update-manager: error: no such option: -c
drew@mission-control:~$



Any ideas?

---

### Post by AtrejuT on 2007-03-08
ok, that might have been my mistake, apparently in badger it is not quite as simple as in later versions.
What you should do is check the version of update-manager you are using. So open up synaptic, find the package update-manager in the long list and see whether the installed version is
0.42.2ubuntu12~breezy1
or higher.

If that is the case open up a terminal and run
sudo update-manager 
without any further options. There should be a button 'check' - press that and it should offer you to update to dapper.

glad to be of help

atreju

---

