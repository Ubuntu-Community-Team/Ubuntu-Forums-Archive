---
title: "Installing in Ubuntu"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-09
Been using Ubuntu 7.04 for about week or so and Like what I see.
I'm very new to linux and seem to always have questions about
some of it's features.

Well, I'd like to install some things and have been using the repository's
I see there are two of them the Add and Remove and one that
is more detailed called Synaptic Package Manager under System.... Administration.

Well, I've seen there are several ways to install something.
for instance I installed Audacity with Add and Remove
It installed everything it needed then put an icon in the Application menu for me
That's very nice, I might add.  I was told Linux wasn't that easy.

Well, I would like to export to Mp3 using Audacity but noticed I need to install
LAME encoder.  With XP I just downloaded the file and placed it where ever I
wanted it ( In my Audacity folder, in program files ).  Well for Linux, it's not that
simple.  I went to the Synaptic Package Manager under System.... Administration
and chose LAME.  Well it installed it but I have no idea where it put it.  This is the
kinda thing I use to get mad about when someone couldn't tell me where they
downloaded their file.  So How does linux go about this. I wasn't offered the
choice where to put it, it just did it.  Is there a special place they go?

I'm thinking about buying an Ubuntu book..... I am a Windows Power User
but not knowing these simple things about an OS make me feel very stupid.

Could someone help me.

thanks

---

### Post by Ek0nomik on 2007-08-09
[http://www.psychocats.net/ubuntu/audacity](http://www.psychocats.net/ubuntu/audacity)

---

### Post by Niklas Schröder on 2007-08-09
do this...

```

ln -s /usr/lib/libmp3lame.so.0 /usr/lib/libmp3lame.so

```

and then link to this file when audacity prompts you.

> 
/usr/lib/libmp3lame.so


---

### Post by Orbital75 on 2007-08-09
Ek0nomik ,
  I looked around and don't see it on /usr/lib

Maybe I downloaded the wrong thing....
Everytime I type ibmp3lame into the Synaptic Package Manager
search bar nothing comes up.
So, I'm thinking it's not installed.

---

### Post by Niklas Schröder on 2007-08-09
why don't you just try letting audacity look for it.  if it works, then all is well.  if not, then come back and ask us.

---

### Post by Hospadar on 2007-08-09
Just a general note, if you are curious where a package's files went, go to the package in synaptic, right-click go to properties, then to installed files.  the package that the library is in is actually called "liblame0" but the library file has a different name.

LAME itself (as installed by the package "lame") is just a command line tool, so you arn't going to find it in the menu.  If you are looking to export to mp3 from audacity, what happens when you go to file->export mp3 from within audacity?

---

### Post by Orbital75 on 2007-08-09
> **Niklas Schröder said:**
> why don't you just try letting audacity look for it.  if it works, then all is well.  if not, then come back and ask us.

Thank you for the help Niklas Schröder but it came back with 
No such file in directory. :(

---

### Post by Niklas Schröder on 2007-08-09
go here. 

[http://sourceforge.net/project/downloading.php?group_id=290&use_mirror=internap&filename=lame-3.97.tar.gz&42014470](http://sourceforge.net/project/downloading.php?group_id=290&use_mirror=internap&filename=lame-3.97.tar.gz&42014470)

take that file, place it somewhere, extract it, "cd" to the extracted folder and do...

```

./configure
make
make install

```

then you can delete the compressed and uncompressed folders.  then use the steps mentioned in one of my previous posts and have audacity look for it.

---

### Post by Orbital75 on 2007-08-09
All done.... thank you.

Seems like alot of work but never less I'm very happy it worked...... 
I want to learn all this but it seems its different everytime......
Did I just compile code?

---

### Post by Niklas Schröder on 2007-08-09
in essence, yes, you did just compile code.  ;)  keep in mind that not everything's this complicated in linux, but some of it is.  that's the price you pay for complete control of your desktop environment.  :)

EDIT: and it's not all complicated.  but the forums and google are your friend.  ;)  just try to make sure what you're trying to do is legal/safe.  don't go to some badly designed text-only site, download something, compile the code, install, and think your machine's gonna be A-OK.  it's best to ask on the forums if you have any questions. 

cheers!

---

### Post by Orbital75 on 2007-08-09
> **Niklas Schröder said:**
> in essence, yes, you did just compile code.  ;)  keep in mind that not everything's this complicated in linux, but some of it is.  that's the price you pay for complete control of your desktop environment.  :)

EDIT: and it's not all complicated.  but the forums and google are your friend.  ;)  just try to make sure what you're trying to do is legal/safe.  don't go to some badly designed text-only site, download something, compile the code, install, and think your machine's gonna be A-OK.  it's best to ask on the forums if you have any questions. 

cheers!


Yes..... I'll agree with you there.
When I want to try something new, I'll just use the repository's.
Their safe right?  All of them?

The Ubuntu Community is great and very helpful just as you guys were
with my audacity issue.  

I'm a very fluent and Security minded Windows user.
I've got my Windows Machined locked down as tight as possible for decent use.
Router, Personal Firewall, Running as a Limited User, Locked Host File, Sandboxed Firefox with No Script installed,
NOD32 AntiVirus, 3 different Spyware Scanners (Adaware,Spybot,Defender).
But I would like an OS where I don't have to worry about all that and I think Ubuntu
is that answer. The only thing is, it's different and I don't understand it ( yet ).


When it comes to Linux, I feel like I'm starting all over again and trying to relearn
everything in a different way.  It took years for me to gain all this Window Knowledge
and feel that learning Linux will take even longer.  However, I do wish to learn.
I'm a visual learner and I think that's why I have such an issue with the command line.
Would you recommend buying a Book?  Would that move things along faster.
I was looking at Ubuntu Unleashed (2nd Edition).

---

### Post by Niklas Schröder on 2007-08-09
yeah.  from what i know, everything in the repositories is all good.  and i used to be an avid windows user as well.  but then i got hit with a BAD virus case and used ubuntu to get my data off the dead operating system.  i've only booted into windows three times since then (once to re-install just cause i payed for it, once to re-install all my programs, and once to set it up so my dad could use it at hotels).  linux may seem intimidating, but it's only taken me three or four months to get where i am now, and i'm pretty helpful in some of the threads.  ;)  just hang in there.  i'd recommend only buying the book if you start to have ALOT of troubles.  there's really so many guides on the net, plus this AWESOME forum, that you probably won't need it after a few weeks anyway!  :)  good luck!  and feel free to pm/e-mail me if you need any more help.  ;)

cheers!

p.s.  i felt EXACTLY like you do now when i first started out.  feel free to ask questions on the forum, no matter how "dumb" you think they may be.  this is really an GREAT community.  :)

---

