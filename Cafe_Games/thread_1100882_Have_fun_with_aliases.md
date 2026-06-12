---
title: "Have fun with aliases"
date: 2009-03-19
forum: Cafe Games
---

### Post by SlickRick on 2009-03-19
I've decided to make a thread where you can post funny aliases for commands.
These are some examples from the [YKYAGW]("http://ubuntuforums.org/showthread.php?t=86237&page=527") thread.
It started with a lolspeak reference...

> **SlickRick said:**
> YKYAGW yur .bashrc file now looks like dis
```
alias do_want='sudo apt-get install'
alias do_not_want='sudo apt-get remove'
alias i_can_haz='sudo apt-get install'
alias im_in_yur='cd'
alias kthxbai='exit'
alias invisbl='fg' #send job to foreground
alias visabl='echo'
alias caturday='date'
alias not_amuzed='killall'
alias oh_noez='reboot'
alias nomnomnom='rm'
alias rly='sudo'
```

If anyone haz suggestions on how I could improve it, plz feel free to mention them but those are the commands I mostly use. Apart from 'fg' but I couldn't have visabl and not have invisabl.

> **GepettoBR said:**
> I tip my hat to you, and I have some suggestions:

```
alias longcat='less'
alias all_ur_base='cd /'
alias d00d='man'
alias lolcat='cat'
alias OC='sudo apt-get update'
alias srs_bsns='sudo su'
```

EDIT: Does alias accept wildcards? If so, 
alias wat $1='$1 --help'
is also funneh.

you add these to your .bashrc file in your home folder. To edit it, simply type ```
sudo gedit ~/.bashrc
```

---

### Post by s.fox on 2009-03-19
Yay,  LOL CODE (sort of)

---

### Post by jenkinbr on 2009-03-19
Add the line ```
alias icanhaz='sudo apt-get install'
``` to your ~/.bashrc

Add the following ```
#!/bin/bash
echo "<inseart list of packages to install here>";
``` to the file '~/bin/cheezburger', replacing the angle-bracketed text with the packages you want to install, seperated by a space. Then chmod it to 0744.

then, using the above, run ```
icanhaz `cheezburger`
```

---

### Post by jenkinbr on 2009-03-19
```
alias give_me_teh_lolz='fortune'
```

You *MAY* need to install some of the extra fortune cookie packages from synaptic for this to really give you 'teh lolz'.

---

### Post by crazyness003 on 2009-03-19
too much. :lolflag:

---

### Post by crazyness003 on 2009-03-19
alias "shoopdawhoop"="echo BLRAAA"

---

### Post by linuxisevolution on 2009-03-19
```


alias soud="sudo"

alias die="sudo halt"

alias kill="xkill"

alias iwant="sudo apt-get install"

alias entertainme="xmmc"

alias dance="echo no"

alias whosyourmother="echo your mom"


```

:D

---

### Post by jenkinbr on 2009-03-19
> alias kill="xkill"

May not work because kill is an actual program name.

```
alias bump='firefox -url http://ubuntuforums.org/showthread.php?t=520091'
```

---

### Post by linuxisevolution on 2009-03-19
> **jenkinbr said:**
> May not work because kill is an actual program name.

```
alias bump='firefox -url http://ubuntuforums.org/showthread.php?t=520091'
```

that alias works, I've used it.

```


winrid@winrid-desktop:~$ find_devon
Are_you_out_of_your_mind?_You_just_had_rm_delete_him!
winrid@winrid-desktop:~$ 


```

---

### Post by SlickRick on 2009-03-20
Heir's sum moar I'v thunk ov
```
alias hoomin='man'
alias visabl='ls'
alias invisabl='clear'
alias teh_interwebz='ipconfig'
alias internet_tubes='ipconfig'
alias ur_doin_it_rong='false'
alias ur_doin_it_rite='true'
alias ceilin_cat='su'
alias moar='more'
alias monorailcat='mv'
alias pewpewpew='xkill'
```

[IMG]http://icanhascheezburger.files.wordpress.com/2008/03/funny-pictures-rabbit-eats-thread.jpg[/IMG]
I couldn't resist :D

---

### Post by GepettoBR on 2009-03-20
> **SlickRick said:**
> alias pewpewpew='xkill'
Awesome :)

```
alias goodnight_sweet_prince='sudo shutdown -h now'#halt
alias brb='sudo shutdown -r now'#reboot
```

---

### Post by SlickRick on 2009-04-07
does anyone know how to change bash autput, like instead of "Sorry, try again" for an incorect password it could say "EPIC FAIL, u typedz in teh rong paswurdzor"

---

### Post by jenkinbr on 2009-04-07
I think those are built in to bash and sudo and such.  You *could* try to mod them with a hex editor, although I would not try this. Better yet, rebuid them from source. ;)

---

### Post by GepettoBR on 2009-04-07
> **jenkinbr said:**
> I think those are built in to bash and sudo and such.  You *could* try to mod them with a hex editor, although I would not try this. Better yet, rebuid them from source. ;)

If we're on the subject of rebuilding it from source, we could embed the aliases in the new version, and it would be the birth of a new package: lolbash.

Of course, a part of it'd be Debian-only, since it aliases apt-get... though through a build script we could probably probe the system to see what package manager it uses and select the appropriate aliases for yum, pacman, etc... it would no doubt be a fun project, albeit a completely useless one.

---

### Post by SlickRick on 2009-04-08
I would be up for it, if I knew how to actually do that. I got a cool name though, the :lolflag:-again shell. You see what I did there?

---

### Post by GepettoBR on 2009-04-08
> **SlickRick said:**
> I would be up for it, if I knew how to actually do that. I got a cool name though, the :lolflag:-again shell. You see what I did there?

Yes, I do. And the acronym is cool as well: Lash.

---

### Post by Penguin Guy on 2009-04-16
I'm going to call it lolscript.
I would advise using [[COLOR="Blue"]this[/COLOR]]("http://ubuntuforums.org/showpost.php?p=7082113&postcount=19") technique of adding lolscript.
Also '[COLOR="Green"]sudo gedit ~/.bashrc[/COLOR]' - sudo is not necessary.

---

### Post by sisco311 on 2009-04-16
> **SlickRick said:**
> does anyone know how to change bash autput, like instead of "Sorry, try again" for an incorect password it could say "EPIC FAIL, u typedz in teh rong paswurdzor"

*Teh Simpsons Already Did It*

```
export VISUAL=gedit && sudo -E visudo
```
append the *Defaults* line with *, insults*
```
Defaults env_editor, insults
```

```
sudo -K
sudo echo insults #type an incorrect password
Password: 
Take a stress pill and think things over.
Password: 
You gotta go owwwww!
Password: 
No soap, honkie-lips.
sudo: 3 incorrect password attempts

```

or if for a custom message:
```
Defaults env_editor, badpass_message="EPIC FAIL, u typedz in teh rong paswurdzor!!!"
```

```
sudo -K
sudo echo f00l
Password: 
EPIC FAIL, u typedz in teh rong paswurdzor!!!

```

---

### Post by Penguin Guy on 2009-04-16
**How to Make a dedicated Lolscript Folder**
Feel free to replace lolscript with a name of your choice.

Open terminal and type:
```
gedit ~/.bashrc
```
It will open a file; copy and paste this at the end:
```
# Lolscript:
if [ -f ~/lolscript ]; then
    . ~/lolscript
fi
```

Save the file, quit gedit, go back to the terminal and type:
```
cat > lolscript
```

Now exit the terminal, open Nautilus and browse to your home directory. You should see a file called lolscript. You can add any aliases you want in there, and if there are any problems; just delete the file and reboot, all will be returned to normal.

*Have fun!*

---

### Post by Penguin Guy on 2009-04-16
Somebody has already thought of something like this, lol!
```
HAI
CAN HAS STDIO?
I HAS A VAR
IM IN YR LOOP
	UP VAR!!1
	VISIBLE VAR
	IZ VAR BIGGER THAN 10? KTHXBYE
IM OUTTA YR LOOP
KTHXBYE
```
I guess I'll just call it Roflscript instead...

---

### Post by kpatz on 2009-04-16
Here's some I just thunked up:

alias gimme='sudo apt-get install'
alias getlost='sudo apt-get remove'
alias goaway='rm'
alias please='sudo'
alias stupid='bash --restricted'
alias sudont='sudo -k'
alias ciao='logout'
alias moo='apt-get moo'
alias cow='apt-get moo'

---

### Post by jenkinbr on 2009-04-16
> **kpatz said:**
> Here's some I just thunked up:

alias gimme='sudo apt-get install'
alias getlost='sudo apt-get remove'
alias goaway='rm'
alias please='sudo'
alias stupid='bash --restricted'
alias sudont='sudo -k'
alias ciao='logout'
alias moo='apt-get moo'
alias cow='apt-get moo'
apt-get requires sudo, so 

alias moo='sudo apt-get moo'
alias cow='sudo apt-get moo'

---

### Post by GepettoBR on 2009-04-16
Setting
alias OMG_HOW_DID_I_GET_HERE_I_AM_NOT_GOOD_WITH_COMPUTER='pwd'
isn't very practical.

---

### Post by sisco311 on 2009-04-16
> **jenkinbr said:**
> apt-get requires sudo, so 

alias moo='sudo apt-get moo'
alias cow='sudo apt-get moo'

nope, you can run some of the apt commands as an user:
```
apt-get moo
apt-cache search moo
apt-cache show xtux
```

```

alias jenk='sudo apt-get'
alias in='install'
alias br='brain'
$jenk in br
```
/bad joke

---

### Post by jenkinbr on 2009-04-16
> **sisco311 said:**
> nope, you can run some of the apt commands as an user:
```
apt-get moo
apt-cache search moo
apt-cache show xtux
```

```

alias jenk='sudo apt-get'
alias in='install'
alias br='brain'
$jenk in br
```
/bad joke
Last time I tried running apt-get moo, I got an error, something like "apt-get: need to be root"

---

### Post by SlickRick on 2009-04-16
> **GepettoBR said:**
> Setting
alias OMG_HOW_DID_I_GET_HERE_I_AM_NOT_GOOD_WITH_COMPUTER='pwd'
isn't very practical.

:lolflag:

---

### Post by Penguin Guy on 2009-04-16
Sorry just had to post this again. :p

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=110005&d=1239902826[/IMG]

---

### Post by SlickRick on 2009-05-20
alias huggz='touch'

---

### Post by Penguin Guy on 2009-05-20
```
alias ceiling_cat_says:='sudo'
alias plz_help_look_for_word='grep'
```

---

### Post by sisco311 on 2009-05-20
alias whattimeisit='notify-send "Time:" $(date +%H:%M)'

---

### Post by lukjad on 2009-05-20
alias SlickRick='cd /dev/null/'

:p ;)

---

### Post by SlickRick on 2009-05-20
alias lukjad007='haha_how_original'

---

### Post by GepettoBR on 2009-05-20
alias both_of_you='children'

---

### Post by lukjad on 2009-05-20
alias GepettoBR='hypocrite'

---

### Post by Marlonsm on 2009-05-20
```

alias halp_me='man'

```

only one I can think of right now...

---

### Post by lukjad on 2009-05-20
alias wut='what'
alias what='who'
alias who='how'
alias how='why'
alias why='help'
alias help='mayday'
alias mayday='SOS'
alias SOS='S.O.S.'
alias S.O.S.='confused'
alias confused='confuddled'
alias confuddled='wut'

---

### Post by lukjad on 2009-05-20
alias nuke ='destroy'
alias destroy='obliterate'
alias obliterate='crush'
alias crush='smash'
alias smash='pound'
alias pound='grind'
alias grind='Death_Star'
alias Death_Star='MS_Vista'
alias MS_Vista='BSOD'
alias BSOD='Kernel_Panic'
alias Kernel_Panic='Horsemen'
alias Horsemen='Pestilence'
alias Pestilence='War'
alias War='Famine'
alias Famine='Death'
alias Death='sudo [censored to not get in trouble with the mods]'

---

### Post by lukjad on 2009-05-20
alias fun='good_times'
alias good_times='rock_and_roll'
alias rock_and_roll='music'
alias music='not_rap'
alias not_rap='music'
alias classical='music'
alias BigBand='music'
alias reggae='music'

---

### Post by SlickRick on 2009-05-21
you can only have one alias per command. If you write one and then another one, the second one over-writes it

---

### Post by lukjad on 2009-05-21
Spoilsport. :p

Anyway, I think this thread left the realm of reality a long time ago. ;)

---

### Post by Penguin Guy on 2009-05-21
> **lukjad007 said:**
> Spoilsport. :p

Anyway, I think this thread left the realm of reality a long time ago. ;)
Oh no, my lolscript file is very real thank you. :p
The toggler script is also very real. :p

---

### Post by SlickRick on 2009-05-21
I don't really see the point in that toggler script, since you can still use the original commands even if they have aliases

for example,
> alias pewpewpew='xkill'
allows me to say pewpewpew when I want to get the little skull up and close an unresponding window. However, typing xkill still has the same effect.

---

### Post by Penguin Guy on 2009-05-24
You have a point - I'll probably keep it on all the time now.

---

### Post by lukjad on 2009-05-27
alias sudu='try_again'
alias sodu='nope'
alias dosu='NO'
alias duso="sigh"
alias sdou='nononononononono'

---

### Post by unicycletim on 2009-05-27
these are awesome. i copied heaps. here are my ones
```
alias pwn='rm'
alias beyeclean='sudo apt-get autoremove'
```

---

### Post by SlickRick on 2009-05-27
> **lukjad007 said:**
> alias sudu='try_again'
alias sodu='nope'
alias dosu='NO'
alias duso="sigh"
alias sdou='nononononononono'

I laughed at first but this doesn't make sense now. Neither of those are commands, so I don't think you can alias them and what's the point?. If you type in "nope" it would be the same as typing in "sodu" and the terminal would echo "bash: sodu: command not found"

---

### Post by jenkinbr on 2009-05-27
> **unicycletim said:**
> these are awesome. i copied heaps. here are my ones
```
alias pwn='rm'
alias beyeclean='sudo apt-get autoremove'
```

I would rather see pwn as:

```
alias pwn='chown jenkinbr:jenkinbr'
```

Of course, you would have to replace the 'jenkinbr:jenkinbr' with your <username>:<groupname>

---

### Post by Penguin Guy on 2009-05-27
> **lukjad007 said:**
> alias sudu='try_again'
alias sodu='nope'
alias dosu='NO'
alias duso="sigh"
alias sdou='nononononononono'
> **SlickRick said:**
> I laughed at first but this doesn't make sense now. Neither of those are commands, so I don't think you can alias them and what's the point?. If you type in "nope" it would be the same as typing in "sodu" and the terminal would echo "bash: sodu: command not found"
```
alias sudu='echo "try again"'
alias sodu='echo "nope"'
alias dosu='echo "NO"'
alias duso='echo "sigh"'
alias sdou='echo "nononononononono"'
```
Better?

---

### Post by lukjad on 2009-05-27
> **SlickRick said:**
> I laughed at first but this doesn't make sense now. Neither of those are commands, so I don't think you can alias them and what's the point?. If you type in "nope" it would be the same as typing in "sodu" and the terminal would echo "bash: sodu: command not found"

> **Penguin Guy said:**
> ```
alias sudu='echo "try again"'
alias sodu='echo "nope"'
alias dosu='echo "NO"'
alias duso='echo "sigh"'
alias sdou='echo "nononononononono"'
```
Better?

Thanks. That was what I was going for, but didn't know how. :)

---

### Post by SlickRick on 2009-05-27
I'm confuzzeled

---

### Post by Penguin Guy on 2009-05-28
> **SlickRick said:**
> I'm confuzzeled
When he said 'alias duso="sigh"', he *meant* to say 'alias duso="**echo** 'sigh'"'.

---

### Post by SlickRick on 2009-05-28
> **Penguin Guy said:**
> When he said 'alias duso="sigh"', he *meant* to say 'alias duso="**echo** 'sigh'"'.
I figured it out :p

These two came to me in my sleep
```

alias who_you_gonna_call?='echo ghost busters'
alias stop='echo hammer time'
```

I'm also trying to think of a way to rickroll someone using the terminal

---

### Post by jenkinbr on 2009-05-28
> **SlickRick said:**
> I figured it out :p

These two came to me in my sleep
```

alias who_you_gonna_call?='echo ghost busters'
alias stop='echo hammer time'
```

I'm also trying to think of a way to rickroll someone using the terminal
alias rr='firefox [http://www.youtube.com/watch?v=RSsJ19sy3JI](http://www.youtube.com/watch?v=RSsJ19sy3JI)'

That should do it.

---

### Post by learningcurb on 2009-06-06
How could this thread be complete without:
```
alias moo='aptitude -vvvvvv moo'
```

---

### Post by SlickRick on 2009-06-06
> **learningcurb said:**
> How could this thread be complete without:
```
alias moo='aptitude -vvvvvv moo'
```

someone already mentioned that on page three. You obviously didn't read the whole thread and therefore, your life isn't complete :p

---

### Post by DemonBob on 2009-06-06
> **jenkinbr said:**
> alias rr='firefox [http://www.youtube.com/watch?v=rssj19sy3ji](http://www.youtube.com/watch?v=rssj19sy3ji)'

that should do it.

LMAO, not meaning to hijack but i did something similar to a college before on one of our Linux Test Servers that he logs into develop web apps. Pasted this in the bottom of his .bashrc

```

echo "WATCHME"
echo " "
echo "http://www.youtube.com/watch?v=oHg5SJYRHA0"
echo " "
echo " "

echo "Did you watch the video? (y/n)"
read
case $REPLY in
  yes|y) echo "You have just been RickRoll'd, Complments of the SysAdmin :)";;
   no|n) echo "Awwwwww" exit 0;;
    *) echo "Usage:..." ;;
esac


```

---

### Post by KIAaze on 2009-06-08
> **jenkinbr said:**
> ```
alias give_me_teh_lolz='fortune'
```

You *MAY* need to install some of the extra fortune cookie packages from synaptic for this to really give you 'teh lolz'.

Use the script from [here]("http://arstechnica.com/open-source/news/2008/02/you-can-has-lolcats-with-ruby-and-gtk.ars") instead of fortune. :)

---

