---
title: "Totem says 'could not read from resource'"
date: 2008-01-19
forum: Absolute Beginner Talk
---

### Post by walsworth on 2008-01-19
Hi - 

I'm trying to play a DVD on the Totem Movie Player... right now every time I try to do so, I get an error message that says 'could not read from resource'.

Previous to the message the DVD player had several [suggested by my computer] programs installed for it, which I thought would help, but the end result was this message appearing for the first time.

Help, please! My roomate's having a movie marathon with his girlfriend, and this is my only hope.

---

### Post by glenna on 2008-01-20
You might check out this forum:  [http://ubuntuforums.org/showthread.php?t=672613](http://ubuntuforums.org/showthread.php?t=672613)

I was using totem-xine and now I am back to totem gstreamer...this guy that has been helping me is very good....maybe he can help us both.

Glenn

---

### Post by SunnyRabbiera on 2008-01-20
you may need libdvdcss, as most commercial DVD's dont work by default sorry to say.

---

### Post by walsworth on 2008-01-20
Where would I find libdvdcss? I'm sorry, I should probably know that, but it doesn't show up in my add/remove programs, so I am not sure where else to look.

---

### Post by walsworth on 2008-01-20
Nevermind... found it.

---

### Post by SunnyRabbiera on 2008-01-20
thats good, just keep in mind that the list of packages found in the add/remove app is limited, for more advanced installation I suggest using synaptic.

---

### Post by cammy1174 on 2008-03-01
Sunny,

I am having the same error, installed everything the player asked for, and still get the error.  I tried installing libdvdcss and got the following : 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libdvdcss is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libdvdcss has no installation candidate


In Synaptic, libdvdcss isn't there, and I have libdvdnav4 & libdvdread3 installed.


I have also tried VLC and MPlayer, but when I hit play nothing happens, so I assume they can't play it either.

Thanks in advance for your help!

---

### Post by van_Zeller on 2008-05-05
Same problem here...can someone help?

---

### Post by ubuntu-freak on 2008-05-09
If it cannot find libdvdcss2, you don't have the Medibuntu repo added. See part 1 and 4 of my [how-to](http://ubuntuforums.org/showthread.php?t=766683).
 
Nathan

---

### Post by macness on 2008-06-15
I been having this error as well.  Since it's started I can't: 

[LIST]
[*]Watch some DVD's without getting this message
[*]Use DVD::RIP to successfully rip my movies
[*]Sometimes just even pull data from a data DVD
[/LIST]

I tried using another DVD-R to see if it would help but I get the same thing :(

Any suggestions?

---

