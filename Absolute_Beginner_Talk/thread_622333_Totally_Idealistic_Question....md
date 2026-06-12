---
title: "Totally Idealistic Question..."
date: 2007-11-24
forum: Absolute Beginner Talk
---

### Post by coronalox on 2007-11-24
The way linux has been functioning has produced a very unfamiliar, almost unsettling feeling with me. Of course the little things about linux such as quick boot-up times and the ability to kill any broken app immediately is fantastic. I work as a sys admin in exclusively windows environments so my question is pretty simple but vague I suppose.  How do I change my thinking for a linux environment. I'm so hard-wired for windows that I feel like I'm almost flying blind with linux. In some cases it's simple. I know what I want to do I just don't know how to do it. Therefore, I'm armed with the terminology and google search engine to accomplish most tasks. There are instances though i.e. when an app stalls the system that I have no clue what to do next. In windows I simply hit alt+ctrl+del and close the app or process that is suspect. However, in Gutsy, I can't open the "System Monitor" and cloe that program. I know this this my thread is very cryptic but I'm just trying to wrap my head around Ubuntu.  I'm not dual-booting. I'm an exclusive Linux user now for three weeks.  Maybe it will just take time to get acquainted with my new OS or maybe I'm missing  something. In any event, Beryl didn't draw me in to your community. Your community drew me in. Thanks for having me :)

---

### Post by markharding557 on 2007-11-24
ubuntu has a system monitor where you can close processes
system-->administration-->system monitor-->processes-->right click
and welcome to ubuntu

---

### Post by dips_xe on 2007-11-24
well, to kill an app just open up a terminal and put in "xkill" (without quotations) and click on the app you want to terminate.

i felt the same way you feel when i first started using linux, but you get used to it. the biggest hurdle is becoming comfortable with the command line and learning the complex directory, and what all the config files are and where they are stored. now i'm more comfortable using linux, and windows methods feel weird to me. i think linux is pretty easy to use, os x is much more foreign to me. there's such a variety of ways to do ANYTHING it in linux that it can be overwhelming, but in the end it is more liberating.

---

### Post by jken146 on 2007-11-24
The command for System Monitor is gnome-system-monitor.  You can also hit Alt+F2 and type xkill to get an x for your pointer which kills any program you click on.  If your GUI completely locks up you can restart X with Ctrl+Alt+Backspace, or to kill a single process, Ctrl+Alt+<F1-F6> for a terminal (Ctrl+Alt+F7 brings you back into X).  Use the command ```
pgrep <program>
``` or ```
pgrep -u <user> <program>
``` to find the process ID of a running program, then use ```
kill <PID>
``` to kill that process.  Hope this helps!

---

### Post by annda on 2007-11-24
hi and welcome,

there you have a few suggestions from an average linux user (maybe some gurus will chip in later).

alt+f2 gives you a command popup, where you can quickly invoke xkill - this will turn the cursor into a skull with which you can kill any gui app.

in the terminal, you can use top (another command) to list all the processes and kill the nasty ones - just hit k and enter the process's PID.

if the system is badly beyond responding to those 2 ways, you can 1) kill the xserver (graphical environment) with alt+ctr+backspace, or 2) try logging in into another virtual console (ctr+alt+f1 to f6) and use top there - or kill if you know the process's name.

---

### Post by Daveski on 2007-11-24
> **coronalox said:**
> How do I change my thinking for a linux environment. I'm so hard-wired for windows that I feel like I'm almost flying blind with linux. In some cases it's simple. I know what I want to do I just don't know how to do it. Therefore, I'm armed with the terminology and google search engine to accomplish most tasks.

I understand what you mean, and my advice is to try to understand the system at a deeper level than whichever GUI / Windows manager (or GUI tool-set) you have installed. This is why the terminal is your friend - are you comfortable with the Windows command line? I don't just mean simple directory navigation, but rather are you happy with batch files, can you do fairly complex tasks?

Windows and Linux (and other OSes) do share quite a lot of common concepts. All x86 PC's start up in similar ways, via the BIOS and then onto the bootloader. The kernel of the OS is loaded and then loads of services and usually a GUI. All these concepts are the same, and the deeper down you go, the more alike different systems become.

My advise is to try to learn the underlying concepts and mechanisms of Linux rather than just which GUI tool does which job. With this knowledge you should be happy in any Linux distro - and weirdly you will learn more about Windows as well.

---

### Post by coronalox on 2007-11-24
Wow. I'm thoroughly impressed by the quality of all of your posts. Thank you for taking the time out of your day to respond to my questions. You have all validated my decision to jump right into linux head first. As I become more adept I think you'll see my "bean" rating rise. Next time around I'll be contributing to others! Thanks again, everyone!!!

---

### Post by gn2 on 2007-11-24
There's a utility you can add to the panel that will help with "killing" hung apps. Can't for the life of me remember what it's  called though.

Right click in the panel and try to Add a new item and see if it's in the list.

---

### Post by LaRoza on 2007-11-24
> **coronalox said:**
> How do I change my thinking for a linux environment. I'm so hard-wired for windows that I feel like I'm almost flying blind with linux. In some cases it's simple. I know what I want to do I just don't know how to do it. 

You'll learn in time.

Now Windows seems unwieldly and klunky although I do know a lot about it, *nix grows on you.

There are usually many ways of doing something, but the command line way is generally universal.

To list processes:

```

ps -L

```

You can then kill them with "kill".

Here, you might like this: [http://www.ss64.com/bash/](http://www.ss64.com/bash/) (Its the man pages)

---

### Post by perdition79 on 2007-11-24
I understand the whole "getting into linux" mindset.  I'm still thinking "windows" with everything.  I was chugging along with Ubuntu for about a week, just getting used to the browser, open office applications, playing music.  Then I tried to install UT2004, and was completely lost. 

I picked up a big, thick book called "Ubuntu Unleashed" for about $50 USD. (That probably converts to about five or six Euros now.)  The book is great, especially for a decade-long Windows user like myself.  All I knew from Windows fits into the first hundred pages of this 800 page book.  $50 sounds like a lot of money until you compare it to the cost of upgrading a 7-year-old computer and buying Vista.  (I can prove my computer's old: glxgears runs at 458.115 fps with the nvidia drivers installed.)

---

### Post by buccaneere on 2007-11-25
> **jken146 said:**
>  ...  If your GUI completely locks up you can restart X with Ctrl+Alt+Backspace, ...  

I just did that successfully.

I think I should first have brought up a list of running processes to see what one was hangin', huh? What is the command for that?

Thanks!

---

### Post by supersonicdarky on 2007-11-25
Also, if your system hangs and ctrl+alt+bksp or anything else doesn't work, press and hold alt+prntscr and type r-e-i-s-u-b while holding the two keys. This is a safer option to reseting as it kills all tasks and unmounts all drives before rebooting.

[**[More Info]**](http://fosswire.com/2007/09/08/fix-a-frozen-system-with-the-magic-sysrq-keys/)

---

