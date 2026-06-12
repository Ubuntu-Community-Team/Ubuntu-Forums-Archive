---
title: "Can't input password in terminal"
date: 2006-04-05
forum: Absolute Beginner Talk
---

### Post by Drew555 on 2006-04-05
Oi oi there people,

Another noob on the trail of some info. I am really new, so bear with me...

I'm trying to get java to work on firefox, I'm following a step by step, but it doesn't mention what to do when you type in the su command and it asks you for a password then doesn't let you type it in.

Am I missing something really simple here?

The terminal works ok (I think...), but when it asks for the password, the only key that does anything is the enter key.

I'm fresh from windows, and enjoying the challenge (even went and got an ethernet card so my router would work) but this is a little strange, to say the least.

Many thanks in advance.

Drew

---

### Post by Princey on 2006-04-05
[QUOTE=Drew555]Oi oi there people,

Another noob on the trail of some info. I am really new, so bear with me...

I'm trying to get java to work on firefox, I'm following a step by step, but it doesn't mention what to do when you type in the su command and it asks you for a password then doesn't let you type it in.

Am I missing something really simple here?

The terminal works ok (I think...), but when it asks for the password, the only key that does anything is the enter key.

I'm fresh from windows, and enjoying the challenge (even went and got an ethernet card so my router would work) but this is a little strange, to say the least.

Many thanks in advance.

Drew[/QUOTE]

Not really. It's by design that when you type your password it doesn't show the **** you're used to seeing in Windows. Just go ahead and type your password even if you don't see a thing. Press enter when done and the rest will flow.

---

### Post by Perfect Storm on 2006-04-05
You need to use sudo instead of su.
You might check this for java for ubuntu: [http://ubuntuforums.org/showthread.php?t=76735&highlight=java](http://ubuntuforums.org/showthread.php?t=76735&highlight=java)

---

### Post by aysiu on 2006-04-05
Don't ```
su
```
Use ```
sudo
``` instead.

Also, when you enter your password in the terminal, there's no visual feedback--no asterisks, nothing to indicate how many characters you're typing in. It's still accepting your password--it just isn't showing you anything.

---

### Post by ferebee on 2006-04-05
[QUOTE=Drew555]Oi oi there people,

Another noob on the trail of some info. I am really new, so bear with me...

I'm trying to get java to work on firefox, I'm following a step by step, but it doesn't mention what to do when you type in the su command and it asks you for a password then doesn't let you type it in.

Am I missing something really simple here?

The terminal works ok (I think...), but when it asks for the password, the only key that does anything is the enter key.

I'm fresh from windows, and enjoying the challenge (even went and got an ethernet card so my router would work) but this is a little strange, to say the least.

Many thanks in advance.

Drew[/QUOTE]

When you type your password for sudo in terminal no characters show up on the screen, but they are going in there.

---

### Post by Drew555 on 2006-04-05
Many many thanks for your mega speedy replies, guys.

Thanks for letting me know about the invisi-password thing, but it seems to not like my password. I read elsewhere that on installation ubuntu chooses it's own password, if this is right, where can i find it?

Oh, and it cant find java-package.....

Drew

---

### Post by aysiu on 2006-04-05
[QUOTE=Drew555]
Thanks for letting me know about the invisi-password thing, but it seems to not like my password. I read elsewhere that on installation ubuntu chooses it's own password, if this is right, where can i find it?[/QUOTE] Ubuntu doesn't choose its own password.

You choose a user in the installation and a user password. This user has administrative privileges and can temporarily assume root privileges by typing *sudo* in front of commands. Once *sudo* is typed, you can enter your user password.

If you type *su*, you're trying to log into the root account, and Ubuntu defaults to having the root account disabled.

I don't know what instructions you've been following, but try [these](https://wiki.ubuntu.com/RestrictedFormats#head-68565ae07a003332e82c9f23706638777396c249) instead.

---

### Post by Drew555 on 2006-04-05
Cheers aysiu, I've sussed that bit now, you boys really know your onions!

Just need to figure out where my java-package has wandered off to now...

Drew

---

### Post by Perfect Storm on 2006-04-05
[QUOTE=Drew555]Many many thanks for your mega speedy replies, guys.

Thanks for letting me know about the invisi-password thing, but it seems to not like my password. I read elsewhere that on installation ubuntu chooses it's own password, if this is right, where can i find it?

Oh, and it cant find java-package.....

Drew[/QUOTE]

add multiverse to your sourcelist.
```
sudo gedit /etc/apt/sources.list 
```

[b]## Multiverse
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
[/b]
```
sudo apt-get update
```

---

### Post by catlett on 2006-04-05
This is the best thing for someone new to Ubuntu fresh from Windows. An Ubuntu guru put together a script that will apply the basic stuff you need in the beginning(Update your browser with all plug-ins,java,dvd codecs etc). So take advantage of his hardwork and make your life easier. Follow this link and install Automatix it's well worth it. [http://www.ubuntuforums.org/showthread.php?t=138405](http://www.ubuntuforums.org/showthread.php?t=138405)

---

