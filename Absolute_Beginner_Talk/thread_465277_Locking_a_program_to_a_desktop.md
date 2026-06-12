---
title: "Locking a program to a desktop"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by herrma29 on 2007-06-05
A couple questions.

First, is there any way to lock a program to a certain desktop? For example, I always put pidgin on my second desktop, have amarok show on all desktops, and use firefox on my first desktop. Is there any way to make sure that these programs only load on those particular desktops?

And second, is there any way to do this at startup? I was using the sessions tool earlier to add amarok to the startup list, and I'm not entirely sure on what I'm supposed to put in. Would the command just be amarok and the name whatever I feel like choosing? Right now I have amarok in for both, but I just wanted to make sure I am doing that right.


Thanks,

Chris

---

### Post by wormser on 2007-06-05
I do not think you can have desktop icons only appear on one workspace yet.

Just put amarok as the command.  You can always test it by opening up a shell - Applications> Accessories> Terminal.  If the command runs then it will work in session.

---

### Post by herrma29 on 2007-06-06
Thanks for the help! Any idea if that idea is slated for future releases?

---

### Post by Nekiruhs on 2007-06-06
> **wormser said:**
> I do not think you can have desktop icons only appear on one workspace yet.

Just put amarok as the command.  You can always test it by opening up a shell - Applications> Accessories> Terminal.  If the command runs then it will work in session.
I think you may have mis understood the OP, he wnts to know if you can have Windows on a specific desktop. If im right.

---

### Post by Jose Catre-Vandis on 2007-06-06
Try devilspie - its in the repos

---

### Post by Nikron on 2007-06-06
You can do it easily, I do something similar with a program called 'devilspie'.  It's a pretty easy thing to set up, but it does require some configuration file editing...  Anyway, there are several howtos.  And "apt-get devilspie" will grab you the man pages, so you should be set.

---

### Post by Inxsible on 2007-06-06
If you are using MetaCity, you can show programs in all desktops. Right click on the program in the taskbar and select the appropriate thing. If it can be done at startup -- i dont know !! :(

---

### Post by herrma29 on 2007-06-06
I don't suppose you could tell me what exactly I am doing wrong here?

```
<?xml version="1.0"?>
<!DOCTYPE devilspie SYSTEM "devilspie.dtd">
<devilspie>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="pidgin"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="workspace_index" value="2"/>
      </action>
    </actions>
  </flurb>
  <flurb>
    <matchers>
      <matcher name="DevilsPieMatcherWindowName">
        <property name="application_name" value="amarok"/>
      </matcher>
    </matchers>
    <actions>
      <action name="DevilsPieActionSetWorkspace">
        <property name="pinned" value="TRUE"/>
      </action>
    </actions>
  </flurb>

</devilspie>
```

Following this, I did this:

```
chris@chris-laptop:~$ killall devilspie
devilspie: no process killed
chris@chris-laptop:~$ devilspie & will
[1] 21394
No s-expressions loaded, quiting
bash: will: command not found
[1]+  Exit 1                  devilspie
chris@chris-laptop:~$ 

```

I saved my .devilspie.xml file in the directory: /home/chris

---

### Post by boenki on 2007-06-07
hi

you use the old format for settings in devilspie

use a syntax like this

```
(if
	(matches (window_name) "xfce4-terminal")
	(begin
		(skip_tasklist)
		(below)
		(stick)
		(geometry "640x222")
	)
)

```

look here for more [http://wiki.foosel.net/linux/devilspie](http://wiki.foosel.net/linux/devilspie)

---

