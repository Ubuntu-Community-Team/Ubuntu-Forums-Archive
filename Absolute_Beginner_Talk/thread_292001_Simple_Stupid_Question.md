---
title: "Simple Stupid Question"
date: 2006-11-03
forum: Absolute Beginner Talk
---

### Post by Coinnach on 2006-11-03
Hi guys,

Apologies for posting what I am sure is going to be a simple solution but I am a complete newbie with linux and am a little frustrated.

I have built my first ubuntu box, I have installed postfix et al (insert all of the usual add-ons for postfix) and now I am about to start to configure it.

Howeverr I don't know how to make a change to the config files and save it. It tells me I have insufficient rights to save the file to the location - e.g. /etc/shorewall/shorewall.conf

I know people are slapping their foreheads at the moment sorry but I have to ask. I did search the forums and didn't find anything for this.

Also installing spampd and havp I constantly get errors

Havp: is an error to do with File System locking - it tells me I need to use 'mount -o mand', I found on google a Havp developer telling a guy to use 'mount -o remount,mand /' switch which I did but when I ran the install I got the same issue. No idea what to do.

Spampd: is getting an error to do with not getting access to a conf file - need to be root to do this. Any help with this would also be appreciated.

Other than that I have to say that I am enjoying my first forays into the Ubunto Linux world, it is a tidal wave of a learning curve but extremely interesting.

I hope to maybe be able to contribute to the site, maybe a beginner's viewpoint on 'How to install Postfix and friends on Ubuntu 6.10'.

Oh yes I managed to upgrade from Breezy to Dapper to Edgy - really cool upgrade process.

Anyway thanks for any help in advance.

---

### Post by taurus on 2006-11-03
If you need to edit/modify/create file on your system, you need to be root and sudo would give you that permission.  So, run it with sudo from a prompt, Applications -> Accessories -> Terminal...

```
sudo <command>
```

---

### Post by Bachstelze on 2006-11-03
Hi and welcome to Ubuntu :)

You need to be root to edit files outside your home dir. In Ubuntu, you become root by adding sudo after the command you want to run, i.e.

```
sudo nano /etc/shorewall/shorewall.conf
```

---

### Post by Coinnach on 2006-11-03
Great thanks guys, I was trying to access the file either through the GUI and edit or just by typing gedit filename  - I knew there was going to be an easy solution. Thanks again - I'm off to start configuring.

Any takers on the Havp and Spampd errors?

---

### Post by Kulgan on 2006-11-03
or if you want to keep the session as root, type 
```
sudo -s
```
then your root password, and you will be able to do anything from that terminal. 
be sure to log out of root by typing 
```
exit
```

---

### Post by taurus on 2006-11-03
If you want to use gedit as your editor, then use the "gksudo" with it...

```
gksudo gedit <filename>
```

---

### Post by Coinnach on 2006-11-03
Great guys, this will be very helpful.

---

