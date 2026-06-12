---
title: "Desktop Effects problem"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by gazzadtfan on 2007-05-02
Hi 

Could someone help a newbie getting into Ubuntu. 

I currently have 7.04 installed and stupidly clicked on the Desktop Effects button. Now I can't get logged into Ubuntu. It hits me with a black screen with lots of writing, that I don't know what it's talking about. If I go into the safe mode, I'm afraid once it gets into the terminal I don't know what it's looking for or what I should do. 

What I wanted to do was get back into the system to disable the Restricted Drivers, which I thought would do the trick but how do I do that via the terminal?

Thanks in anticipation

Gazzadtfan

---

### Post by GrueTamer on 2007-05-02
The recovery mode should bring you to a gdm screen, but if it doesn't, as long as you're in an X session, you can type

```
startx
```

And you'll be on your way.  But as I recall, it brings up a regular Ubuntu session, just with some tweaks.

---

### Post by gazzadtfan on 2007-05-03
Thanks Gruetamer for your reply.

Unfortunately when I enter startx from the safe mode I get an error - API Mismatch. It states that the NVidia Kernale Module is version 1.0-9755 bu the X Module version is 1.0-9631. It further says to make sure they are both the same and as a result it failed to initialize the NVidia Kernel Module.

Any ideas on how to go about sorting this?

Thanks in anticipation

gazzadtfan

---

### Post by koshari on 2007-05-03
ok you winn need to restore your last xorg config file, 

and you will need to do this in command prompt, yes that scary white writing stuff, but dont despair we will see you through it, first go "cd /etc/X11" then "ls"

and tell us how many xorg files

---

### Post by gazzadtfan on 2007-05-03
Hi koshari

I did as you said, had a look and I've got 3 as follows:

1.  xorg.conf

2.  xorg.conf-backup

3.  xorg.conf-backup-200702132316

There were other files there as well but only the above xorg ones.

Does that make any sense to you?

thanks

gazza

---

### Post by dannyboy79 on 2007-05-21
Don't know if the rc.local solution will work for you like it did me but here's what I found when I got that for the 9755 kernel module being loaded when I really wanted it to load 100.xx.xx.

Just so you are aware, I believe there is a bug in the Envy Unstable script.

 I troubleshot the API mismatch for about 2 hours with the help of a forum user that goes by the screen name psyke83 or somethign very similar to that. HE was helping me thru gaim (IM). 

He tried to have me add blacklist nvidia_new to the /etc/modprobe.d/blacklist file, BUT that still didn't work, NO module was loading when we tried that and that fix DID work for psyke83 so we weren't sure why it didn't work on my machine? I also ensure that my /etc/defaults/linux-blah-blah-blah-common DID have the Disabled MOdules = "nv" within it and it STILL DIDN'T WORKL.

It turned out that the Envy unstable program had a bug and didn't do somethign correctly (if this is an untrue statement, I am only conveying the message that psyke83 informed me of. He said that he tried telling the author of Envy but the author of Envy said there was no bug. Then psyke83 even tried the unstable version on his own computer and tried to install 100.xx.xx and he got the same API mismatch error). 

So the soltuion was to add a hack to my rc.local file so that the correct nvidia kernel module would load. This is what I added BEFORE the exit 0 within the rc.local file:
find /lib/modules/`uname -r` | grep -i nvi | grep -v fb | grep nvidia.ko$ | xargs insmod
and finally the damn 100.xx.xx kernel module would load. BUT to no avail, random freezing is STILL OCCURING!!!! I have posted a million times in various threads about Fiesty freezing on simple tasks, like gedit, or various config dialog boxes opened thru System, Admin or Prefs. ANyway, I thoguht I'd at least let other know about the solution if they get teh dreaded API mismatch error when the nvidia driver is 100.xx.xx but the module being loaded was 9755 when they used Envy Unstable.

---

### Post by gazzadtfan on 2007-05-24
Thanks for all the help. I've managed to sort things out.

gazzadtfan

---

### Post by dannyboy79 on 2007-05-24
can you please please put a brief description of what you did to sort it out as just putting "i've manager to sort it out" does not help other users if they come to this thread due to the title. It's just a good habit to get into, post your resolutions so the whole community can benefit not just you. Thank you.

---

