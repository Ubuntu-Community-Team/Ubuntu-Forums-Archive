---
title: "Cool Custom Bash Prompts"
date: 2008-11-12
forum: Art &amp; Design
---

### Post by LRT on 2008-11-12
i'm not sure if this has been done before, but i was wondering if we could start posting screenshots of unique and cool custom bash prompts... or links to..

---

### Post by LRT on 2008-11-12
for inspiration...

[http://www.gilesorr.com/bashprompt/prompts/](http://www.gilesorr.com/bashprompt/prompts/)

---

### Post by bwhite82 on 2008-11-12
Check out bashish:

[http://bashish.sourceforge.net/](http://bashish.sourceforge.net/)

One (of many themes available) example:

[[IMG]http://img80.imageshack.us/img80/8426/bashishbc7.th.png[/IMG]](http://img80.imageshack.us/img80/8426/bashishbc7.png)

---

### Post by rudihawk on 2008-11-13
What can I change so that it can keep the same functionality, I just want it to say "Yes Master?" as the prompt?

---

### Post by fooey on 2008-11-21
Have you figured this out yet rudihawk? I was going to tell you, but I wasn't sure if you'd come across the answer elsewhere yet.

---

### Post by rudihawk on 2008-11-21
Hey fooey

No I haven't managed to figure it out yet, perhaps you could enlighten me?

---

### Post by Crafty Kisses on 2008-11-21
> **Soldierboy said:**
> Check out bashish:

[http://bashish.sourceforge.net/](http://bashish.sourceforge.net/)

One (of many themes available) example:

[[IMG]http://img80.imageshack.us/img80/8426/bashishbc7.th.png[/IMG]](http://img80.imageshack.us/my.php?image=bashishbc7.png)

That's actually pretty cool.

---

### Post by ABCC on 2008-11-21
Why not see the real thing? Set your background colour to your favourite dark colour and enter


PS1='\[\033[01;39m\]\u@\h \[\033[01;34m\]\W \$ \[\033[00m\]'

to try it out and save it in ~/.bashrc to keep it. To give root a red glow place:

PS1='\[\033[01;31m\]\u@\h \[\033[01;34m\]\W \$ \[\033[00m\]'

in that accounts .bashrc

Admittedly not all that unique by a long shot... but still pretty cool.

Thanks Daniel,

ABCC

---

### Post by emil.s on 2008-11-23
> **ABCC said:**
> Why not see the real thing? Set your background colour to your favourite dark colour and enter


PS1='\[\033[01;39m\]\u@\h \[\033[01;34m\]\W \$ \[\033[00m\]'

to try it out and save it in ~/.bashrc to keep it. To give root a red glow place:

PS1='\[\033[01;31m\]\u@\h \[\033[01;34m\]\W \$ \[\033[00m\]'

in that accounts .bashrc

Admittedly not all that unique by a long shot... but still pretty cool.

Thanks Daniel,

ABCC

Pretty much the same prompt as I'm using:

```
if [ ! `whoami` = root ]; then
	PS1="\[\033[1;32m\]\u@\H\[\033[31m\]:\[\033[34m\] \w\[\033[m\]\[\033[33m\] $>\[\033[37m\] "
else
	PS1="\[\033[31m\]\u@\H\[\033[1;32m\]:\[\033[34m\] \w\[\033[m\]\[\033[33m\] #>\[\033[37m\] "
fi
```

:)

---

### Post by smartboyathome on 2009-01-02
> **rudihawk said:**
> Hey fooey

No I haven't managed to figure it out yet, perhaps you could enlighten me?

Sorry for the semi necro, but I thought I would answer you.

I know how. Just put this in your .bashrc:
```
PS1='Yes, master?'
```
That should do it. :)

---

### Post by rudihawk on 2009-01-03
> **smartboyathome said:**
> Sorry for the semi necro, but I thought I would answer you.

I know how. Just put this in your .bashrc:
```
PS1='Yes, master?'
```
That should do it. :)

Thanks man! :)

---

### Post by smartboyathome on 2009-01-03
> **rudihawk said:**
> Thanks man! :)

Welcome. :)

---

### Post by conlmaggot on 2010-05-18
Can I just say Bashish is great. BUT, as a newbie, I am struggling to get my prompt to change after I have done a sudo su.

What is the best way to highlight the prompt after sudo?

Alternatively, is it possible to have bashish take effect after sudo has been run?

---

### Post by prome7hius on 2011-03-31
I know this thread has been dormant for a while, but just joined the community :)

anyway, here is mine....

&#9484;&#9472;[10:23:45]&#9472;&#9472;[prome7hius]&#9472;&#9472;[Ziggy]:~$
&#9492;&#9472;&#9472;([COLOR=Green]28 files, 3.5Gb[/COLOR])>>


```
 PS1="\[\e[01;37m\]&#9484;&#9472;[\t]&#9472;&#9472;[\[\e[01;37m\u\e[01;37m\]]&#9472;&#9472;[\[\e[00;37m\]${HOSTNAME%%.*}\[\e[01;37m\]]:\w$\[\e[01;37m\]\n\[\e[01;37m\]&#9492;&#9472;&#9472;\[\e[01;37m\](\[\e[32;1m\]\$(/bin/ls -1 | /usr/bin/wc -l | /bin/sed 's: ::g') files, \$(/bin/ls -lah | /bin/grep -m 1 total | /bin/sed 's/total //')b\[\e[01;37m\])>>\[\e[0m\]"
```

---

