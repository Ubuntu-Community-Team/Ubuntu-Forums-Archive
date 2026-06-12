---
title: "what to do when an application does not die using kill command?"
date: 2008-02-06
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2008-02-06
Hi
thank you for reading my post
Is there any way to force an application killing?
I have a process with  which its id is 12478 I tried:
```

kill 12748
sudo kill 12748


```

and it does not die, what can i do?

Thanks

---

### Post by kellemes on 2008-02-06
Sometimes one program may have several processes.
Surely there is some process you need to kill also.

Edit: See here for another option. [http://linux.die.net/man/1/killall](http://linux.die.net/man/1/killall)

---

### Post by philinux on 2008-02-06
I think pkill would work or system monitor.

---

### Post by mysticrider92 on 2008-02-06
First, you can only use the kill command as root (e.g. sudo kill <program>).

If that doesn't work, check to make sure you aren't killing a system process. On occasion, a process will stop working right and not even respond to kill. In that case, you have to reboot the computer.

Just to make sure, what process is it that you are trying to kill?

---

### Post by bwtranch on 2008-02-06
Probably need to re-boot

---

### Post by Trail on 2008-02-06
> **mysticrider92 said:**
> In that case, you have to reboot the computer.

Well, not really. Usually it's something else that needs to be killed as well.

For example, if you try to kill OpenOffice, you need to kill soffice.bin as well. And it's a bit more complex if it's through wine.

---

### Post by kellemes on 2008-02-06
> **Trail said:**
> Well, not really. Usually it's something else that needs to be killed as well.

For example, if you try to kill OpenOffice, you need to kill soffice.bin as well.

Indeed, and that's where [killall]("http://linux.die.net/man/1/killall") comes in handy.

---

### Post by Golem XIV on 2008-02-06
kill does not "kill" a process, it sends a signal.

What you want to do is

```
sudo kill -9 12784
```

All previously posted by others also applies.  Have fun killing stuff!

---

### Post by mysticrider92 on 2008-02-06
> **Trail said:**
> Well, not really. Usually it's something else that needs to be killed as well.

For example, if you try to kill OpenOffice, you need to kill soffice.bin as well. And it's a bit more complex if it's through wine.

Rebooting is just the easier option in most cases. The program could usually be killed or the problem fixed, but if you don't feel like wasting time messing with it, rebooting works...

---

### Post by scorp123 on 2008-02-06
> **mysticrider92 said:**
> First, you can only use the kill command as root (e.g. sudo kill <program>).  **Not true.** A user can kill processes he or she owns. You can't kill processes not belonging to you if you're not "root". Only "root" may kill stuff that belongs to others.

---

### Post by Trail on 2008-02-06
> **mysticrider92 said:**
> Rebooting is just the easier option in most cases. The program could usually be killed or the problem fixed, but if you don't feel like wasting time messing with it, rebooting works...

Yes, but it messes with your uptime! (and if it's over a week, it's such a shame...)

---

### Post by scorp123 on 2008-02-06
> **legolas_w said:**
>  Is there any way to force an application killing? ** kill -9**

> **legolas_w said:**
>  I have a process with  which its id is 12478 I tried:
```

kill 12748
sudo kill 12748 
``` and it does not die, what can i do? Kill or maybe even "kill -9" the parent process. Every process was spawned by "something else". You can easily find out what that "else" was, e.g. with: ```
ps -efH 
```

Example from here:
```
root      5316     1  0 08:17 ?        00:00:00   /usr/sbin/gdm
root      5317  5316  0 08:17 ?        00:00:00     /usr/sbin/gdm
root      5320  5317  1 08:17 tty7     00:04:07       /usr/X11R6/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nol
user       6022  5317  0 08:56 ?        00:00:00       /usr/bin/gnome-session
user       6063  6022  0 08:56 ?        00:00:00         /usr/bin/ssh-agent /usr/bin/dbus-launch --exit-with-session /us
user       6097  6022  0 08:56 ?        00:00:05         gnome-panel --sm-client-id default1
user       6101  6022  0 08:56 ?        00:00:14         nautilus --no-default-window --sm-client-id default2
user       6109  6022  0 08:56 ?        00:00:00         bluetooth-applet
user       6110  6022  0 08:56 ?        00:00:00         update-notifier
user       6112  6022  0 08:56 ?        00:00:00         /usr/lib/evolution/2.10/evolution-alarm-notify
user       6113  6022  0 08:56 ?        00:00:00         glipper
user       6117  6022  0 08:56 ?        00:00:00         nm-applet --sm-disable
user       6118  6022  0 08:56 ?        00:00:00         gnome-cups-icon --sm-client-id default3
``` Notice the hierarchy here? So that's the "genealogy" here, which process spawned which. Let's assume that somehow my entire "gnome-session" was hanging. Fine then: I just "kill -9" the parent process ("gdm" in this case) and this will reset and kill all the programs underneath.

---

### Post by kpkeerthi on 2008-02-06
In addition to all above...
By default the kill command sends TERM signal (graceful exit) to the process you are killing. If the process ignores the TERM signal, it may refuse to stop. You may then use KILL signal instructing the kernel to abruptly kill the process.

**Usage:**
kill -SIGKILL <process>
or
killall -SIGKILL <process>

EDIT: I'm slow :)

---

### Post by ajgreeny on 2008-02-06
Perhaps I'm mistaken but I thought ```
killall application_name
``` would do it eg killall firefox or killall mplayer.  This has only been mentioned once in this thread without any reference to how to use it, so I'm wondering if I am not correct.  However, I know that it is a command I have used many times when things have not died, but there is no gui indication that they are running at all.

---

### Post by scorp123 on 2008-02-06
> **ajgreeny said:**
>  Perhaps I'm mistaken but I thought ```
killall application_name
```  Yes, this works too. But for this to work correctly the name of the task has to be correct.

> **ajgreeny said:**
>  killall firefox or killall mplayer. See above. The name has to be correct. Firefox's binary's name is **/usr/lib/firefox/firefox-bin** .... So you'd have to use: ```
killall firefox-bin
``` ... "killall firefox" won't do anything: ```
> killall firefox
firefox: no process killed
``` ... **killall firefox-bin** however does what you want. It kills each and every instance of Firefox currently running. 

> **ajgreeny said:**
>   However, I know that it is a command I have used many times when things have not died, but there is no gui indication that they are running at all.  Due to the client+server nature of many things that run on Linux it can be that a program's GUI dies but not the actual program itself. I just right now have such a glorious moment: Somehow the connection to my company's IMAP server died and Thunderbird is hanging. I don't see it on my desktop anywhere but "ps -efH" tells me it's still there:```
user      20932     1  0 17:49 ?        00:00:00   /bin/sh /usr/bin/mozilla-thunderbird
user      20936 20932  0 17:49 ?        00:00:00     /bin/sh /usr/lib/mozilla-thunderbird/run-mozilla.sh /usr/lib/mozill
user      20940 20936  0 17:49 ?        00:00:12       /usr/lib/mozilla-thunderbird/mozilla-thunderbird-bin
user      20951 20940  0 17:49 ?        00:00:00         [netstat] <defunct>
```

So to get rid of this dead instance I'd first try to "kill" it ... and if it still doesn't want to move I give it a **"kill -9"**. Or if I am lazy I could also give it a **"killall mozilla-thunderbird-bin"**. :)

---

### Post by seventhc on 2008-02-06
you can try the key combo <Ctrl-Alt-Backspace> if it responds, it will log you out of x and your uptime won't be changed back to 0. :) So you just log back in.

---

### Post by legolas_w on 2008-02-06
Thank you all for reply.
I managed to kill the process using gui based application which is present in gnome, I think its name is gnome-system-monitor.

Thanks

---

### Post by scorp123 on 2008-02-06
> **seventhc said:**
> you can try the key combo <Ctrl-Alt-Backspace>. that one should only be used as a **last resort** as it instantly kills the X-server (= "the graphics driver") and all GUI programs instantly die, e.g. before they have a chance to save their data or settings. But if your GUI hangs badly e.g. after messing around with 3D effects you might also try this.

---

### Post by seventhc on 2008-02-06
I meant it as last resort as opposed to doing a hard cold boot.

---

### Post by ibanez on 2008-02-06
I find 
 xkill works 99.99% of the time

either type xkill into a terminal   or  Alt-F2  xkill

and direct the skull n crossbones at the frozen or stubborn app and click.

Certainly saves rebooting.

---

### Post by bodhi.zazen on 2008-02-06
You can try, in order,

kill PID
killall PID
pkill PID
kill -1 PID
kill -9 PID

with sudo if needed.

Find the PID with 

ps aux | grep <application>

Reboot in linux - Wa ha ha ha ha , good one. :lolflag:

The only time you need to reboot is to change hardware or kernels. There is the (rare ?) system lock up, which is often ( ? always) due to hardware problems, sometimes due to glitches in the (nvidia / ati) video drivers.

To restart a service (server)

sudo /etc/init.d/<service> start/stop/restart

Example :

```
sudo /etc/init.d/apache restart
```

See also : [How to gracefully reboot your Ubuntu/Debian system if all else fails](http://www.arsgeek.com/?p=787)

---

### Post by scorp123 on 2008-02-06
> **ibanez said:**
> I find 
 xkill works 99.99% of the time  Yeap, it's very efficient. I like the cute little Gnome applet you can have so "xkill" is only one mouse click away: Right-click e.g. on the upper panel, then select "+ Add to Panel ..." => Then from the "Desktop & Windows" section select "Force Quit" and drag & drop its icon back onto the panel.

Now when a program misbehaves you can click onto that new icon and with one mouse click send misbehaving GUI programs into digital Nirvana :)

---

### Post by erin06 on 2008-02-26
Thanks for the kill -9 (pid) info. Saved me a lot of time digging around.

---

### Post by angry_johnnie on 2008-02-26
Try searching for all the processes that are related to that particular application.  Open a terminal and type:


ps aux | grep "name of the process"

where "name of the process would be something like "firefox"  or "abiword"


It will give you a list.

Then you could kill each one
Or  kill -9  each one

kill is the nice way.  kill -9 will really force it to go away.

---

### Post by scavenger2008 on 2008-06-18
I never knew about -9, but it really is a lifesaver (in SMOCNIM you only have 2 methods of stopping some bad process, and the first is just like the second - but with a delay :S ) 

Xkill works most of the time, too, and the Force Quit button on a 'grayed-out' app is great.

---

