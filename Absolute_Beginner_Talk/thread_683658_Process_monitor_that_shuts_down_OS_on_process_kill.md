---
title: "Process monitor that shuts down OS on process kill"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by .neo on 2008-01-31
I need a process monitor that shuts down OS on process kill, in particular, it's a firefox browser that's running on a touchpanel kiosk, so if something kills it there should be either an automatic firefox browser restart or ubuntu OS restart (that in turn through session settings will re-run firefox).

I saw on the net an autoprocstart tool which I think does, but that's only in source, and I'd like to find a precompiled package for Gutsy, please.

Thanks for your help.

---

### Post by jan quark on 2008-01-31
do you perhpaps recall the name of the source file ?

---

### Post by emarkd on 2008-01-31
Just a thought here, but how about a script that tests to see if firefox is running and restarts it if it's not?  Something like:

```
!#/bin/bash
firefox &
while true; do
	check=`ps -e | grep -i firefox` 
	if [ ${#check} -lt 1 ]; then    
		firefox &
	fi
	sleep 5
done
```

NOTE:  This is untested code!  I leave it up to the poster to test and debug.

---

### Post by emarkd on 2008-01-31
I suppose I should tell you what my script is supposed to do :)  Name it firefox-forever.sh or something, so you'd do

```
./firefox-forever.sh
```

It would launch firefox (that's the second line). Then it would go into an infinite loop that uses ps every 5 seconds to see if firefox is still running.  If it's not, it restarts it and continues to loop and test.

---

### Post by .neo on 2008-01-31
@emarkd - Thanks for the shell script tip. I'm only a bit uncertain just how stable and CPU demanding that approach will be over the utilizing a specially designed tool like procautostart approach. I'll try it though! Thanks

@jan quark - Here's the page that has a link to autoproxstart.cpp file: [http://www.linuxdocs.org/HOWTOs/Process-Monitor-HOWTO.html](http://www.linuxdocs.org/HOWTOs/Process-Monitor-HOWTO.html)
but I'm unsure what's needed to compile it and have it work on Gutsy. If you know, I'd appreciate the explanation. TIA

---

### Post by emarkd on 2008-01-31
I'm not saying the script is the best way.  You'll have to test it for stability, but there's almost no overhead because of the sleep call in there.

---

### Post by .neo on 2008-02-03
Ok. I've made the loop script as suggested & I've been testing it... Seems to be ok if sleep is set to more than 1 second (with sleep 1 I noticed once - when firefox was stuck on that restore session/start new session question - that the script tried to restart firefox the second time)...

The problem I have now is that gnome doesn't want to start the script itself upon login? At least I don't see the effect of it immediatelly upon login? 

However, if immediatelly after login I try to open a terminal in the just started Gnome session and type in it "ps -e", I do see that bash process was started (there's a line there that goes something like "4465 pts/0 00:00:00 bash")...

I've added a single entry to Startup Programs in System>Preferences>Sessions (disabled/unticked the others). My entry has the following command line "sh /firefox-forever.sh" and I've even changed the chmod on firefox-forever.sh file - which is in / - to mode 4755 <- that means executable, right?!

**EDIT**

*As stated earlier, the bash process starts upon login (which is set to be auto-login in the System>Administration>Login Window>Securit>Enable Automatic Login)...**What I've noticed just now is that firefox starts from that bash process, but in about a minute or so after the login??? Is there anything else going on behind the scenes once the login to Gnome is done that's holding up the effects of that bash script?** *

P.S. (might be of some importance)
_I've just installed minimal Gnome on my machine! Not the whole ubuntu-desktop virtual package, which would be very wasteful in my case..._

---

