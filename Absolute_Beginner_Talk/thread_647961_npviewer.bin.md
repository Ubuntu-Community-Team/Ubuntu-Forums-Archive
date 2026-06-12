---
title: "npviewer.bin"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by Luksion Knight on 2007-12-22
what is it exactly? it opens when i force quit on firefox and it sucks up all my proccessing power.

---

### Post by InGunsWeTrust on 2007-12-24
npviewer.bin is Firefox's Adobe Flash Player plugin. Whenever you have issues with firefox freezing on a page with flash animations try to force quit that process instead. There is a good chance firefox will resume responding and you will merely have to reload the page to get the flash animation back.

---

### Post by Iron_maiden_forever on 2008-01-14
I also have this problem frequently.
Flash player will freeze Firefox.
The solution is to end the process npviewer.bin, but you need to do it quickly, otherwise your downloads may get stuck! (I keep System Monitor running because of that).

Does anyone know a permanent solution to it? Is this an Adobe issue or Ubuntu's?

---

### Post by FuturePilot on 2008-01-14
That's an Adobe issue which they seem reluctant to do anything about.

---

### Post by OsakaWilson on 2008-01-19
Is there a way to  close it through the terminal without opening the system monitor?

---

### Post by Iron_maiden_forever on 2008-01-20
This seems to do the job:

for name in $(ps ux | awk '/npviewer.bin/ && !/awk/ {print $2}'); do kill "$name"; done

---

### Post by Ian Epperson on 2008-01-30
Worse than a freeze.  My cousin was using the comp looking at MySpace vids, and here's the last thing in the logs

```
Jan 13 01:53:28 tigger kernel: [32125.432399] npviewer.bin[23478]: segfault at 0000000000000001 rip 00000000f7a8faf7 rsp 00000000fff808d4 error 4
Jan 13 02:07:11 tigger kernel: [32451.623778] npviewer.bin[23776]: segfault at 00000000f7b2d534 rip 00000000f7a8e0ed rsp 00000000ffd6c020 error 7
Jan 13 02:07:11 tigger kernel: [32451.631667] npviewer.bin[23789]: segfault at 0000000083e58955 rip 00000000f7aac6fe rsp 00000000f5b11b80 error 4
Jan 13 02:13:46 tigger kernel: [32608.437617] npviewer.bin[24023]: segfault at 00000000f7775548 rip 00000000f7a76745 rsp 00000000ffe82080 error 7
Jan 13 02:17:01 tigger /USR/SBIN/CRON[24243]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Jan 13 02:18:07 tigger kernel: [32739.235017] npviewer.bin[24383]: segfault at 0000000000000001 rip 00000000f7afcc76 rsp 00000000ffb095d0 error 4

```

Then the computer died with a short in the motherboard.  I think it was self-inflicted!

---

### Post by InGunsWeTrust on 2008-01-30
Somehow I strondly doubt that flash player killed a motherboard. In all reality a dying motherboard is probably what caused the error in flash player.

---

### Post by uraslacker on 2008-02-05
Ummmm...  I don't think this has anything to do with Adobe.  Isn't this a 64to32 bit wrapper   that happens to be running around Adobe's flash plugin?

In any case, this shouldn't cause any damage.

Cheers,

- Ura

---

### Post by ajaygautam on 2008-02-11
I didn't have any flash running in my browser windows, and this process was at the very top of "top"

well well well... It seems that gmail uses flash (somewhere in there).
I closed the gmail window, and npviewer.bin went away!

---

### Post by toupeiro on 2008-02-12
> **Iron_maiden_forever said:**
> This seems to do the job:

for name in $(ps ux | awk '/npviewer.bin/ && !/awk/ {print $2}'); do kill "$name"; done


Thats one way to do it ... or, you could just do: > pkill npviewer.bin

Personally, I'd just love to find some sort of a real fix to this, from ubuntu or adobe's camp..

---

### Post by cutlerite on 2008-02-20
> **uraslacker said:**
> Ummmm...  I don't think this has anything to do with Adobe.  Isn't this a 64to32 bit wrapper   that happens to be running around Adobe's flash plugin?

In any case, this shouldn't cause any damage.

Cheers,

- Ura

This would definitely describe my situation.

---

### Post by amtriorix on 2008-02-23
Tthere are problems with this npviewer.bin from Adobe.
Always the same s..t with closed source software.
How Linux minded they are !

I saw some reported bugs to lauchpad, including adobe::
[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/179882](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/179882)
[https://www.adobe.com/cfusion/support/index.cfm?event=casedetail&id=0180028487&loc=en_us](https://www.adobe.com/cfusion/support/index.cfm?event=casedetail&id=0180028487&loc=en_us)

Report Your bugs, until they fix it.

---

### Post by arkara on 2008-02-24
ok on my ubuntu installation i have flash working perfectly..
no problem.
but on my fedora install i have a serious problem will every page that has flasg component.
so it should be adobes problem not ubuntu nor fedoras.

---

### Post by Anerum on 2008-02-26
I have the same problem on a 64 bit ubuntu.

---

### Post by BassKozz on 2008-02-27
> **Anerum said:**
> I have the same problem on a 64 bit ubuntu.

ditto :(

---

### Post by easyease on 2008-03-25
same here, this just eats cpu.

---

### Post by cpane on 2008-03-27
I think this is a very serious issue, only because it truly is a usability barrier to Linux adoption to the mainstream. 

I am a long time Linux user, and I love it. But I even am starting to get frustrated that I can't have a typical web browsing experience, and have to constantly keep killing npviewer.bin. 

I like some of the other posters on this topic have a little script that kills it, but I'd like to get it fixed. 

Any ideas what we as a community need to do to get it resolved ? Is the npviewer.bin source available (I'd be willing to look into it if it is (And open)). 

Later

-Chris

---

### Post by InGunsWeTrust on 2008-03-27
It must be just a 64-bit problem because I have 64 bit as well. It may have something to do with the fact that the flash plugin for firefox is actually a 32 bit version that has to be wrapped. Perhaps this is a problem with the wrapper or firefox.

---

### Post by ronocdh on 2008-03-29
> **OsakaWilson said:**
> Is there a way to  close it through the terminal without opening the system monitor?
I think this is a pretty safe way:
```
sudo pkill npviewer.bin
```

---

### Post by cpane on 2008-03-29
This rollback seems to fix the problem for me, see posting by Rashad Tatum, he posted a version of cionci,'s fix  using the package source. I think it just rolls back to an earlier version. 

[https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856](https://bugs.launchpad.net/ubuntu/+source/nspluginwrapper/+bug/177856)

So far so good, My suspect site is [www.cnn.com](www.cnn.com), when you play their videos it hangs npviewer.bin. Same w/ youtube videos. 

I have played probobly 20 videos no issues, I'll post back if the issue comes back. 

-Chris

---

### Post by magrello on 2008-06-11
I'm re-start to use flashblock, and now de problem disapear. Almost, when I want to see a video the npviewer start to suck my cpu.

[https://addons.mozilla.org/pt-BR/firefox/addon/433](https://addons.mozilla.org/pt-BR/firefox/addon/433)

---

### Post by kevin1780 on 2008-06-22
I appreciate all these solutions, but when this happens EVERYTHING locks up. I can't get to the terminal through any means. _ALT+PRINTSCREEN_+R+E+I+S+U+B doesn't work. Niether does _ALT+PRINTSCREEN_+O (to shutdown) for that matter (I inevitably have to hit the power switch).  Of course, CTTL-ALT-BACKSPACE doesn't work either.I entirely freeze up when this happens (mouse curser frozen, too, of course). I don'tknow what to do.

---

### Post by bwallum on 2008-06-30
I'm getting this frequently now. Firefox 3 freezes, I force quit, Up pops a dialogue saying npviewer.bin needs a forced quit, plus another, etc. There is something very odd about this. Is it spyware? Are Adobe trying to suck up personal details like they do in Windows? It seems to happen if a page with some flash is left running for a while without any other inputs.

---

### Post by eudeal on 2008-06-30
> **Anerum said:**
> I have the same problem on a 64 bit ubuntu.
Running AMD64x2(2.8Ghz) w/2 Gb RAM and have encountered npviewer.bin today. Stopped it in the System monitor when it was eating 50% of CPU. Now I have one stopped and one sleeping, that's right 2 npviewer.bin monsters! Will it clone itself every time I stop it? Do I need this piece of crap? I just started noticing in the last few days that my CPU was running about 50% with no apps open. Thought I had been hacked for CPU resource.

---

### Post by wallsensus on 2008-07-03
Hello Everyone,

I'm currently using Hardy AMD64 with the flash installed.  I have a problem with flash for when I am viewing a site with flash on it and then I close the site npviewer.bin dies.

To illustrate this example go to [www.youtube.com](www.youtube.com) in one tab, and [www.futureshop.ca](www.futureshop.ca) in another.

The future shop site seems to be the killer in this case because when I close that tab I get this error from npviwer.bin
```

(npviewer.bin:19293): Gdk-WARNING **: GdkWindow 0x40001bc unexpectedly destroyed

(npviewer.bin:19293): Gdk-WARNING **: GdkWindow 0x40001b9 unexpectedly destroyed

(npviewer.bin:19293): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed
The program 'npviewer.bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 4124 error_code 3 request_code 2 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

```

I've installed everything as per instructions in threads here on ubuntu forums

is anyone else getting this error?  Thanks

---

### Post by reilus on 2008-07-12
> **Iron_maiden_forever said:**
> This seems to do the job:

for name in $(ps ux | awk '/npviewer.bin/ && !/awk/ {print $2}'); do kill "$name"; done

How does this work, do I type this verbatim in the terminal and it kills the program?  I'm having the same problem.....

Could you please elaborate?

---

### Post by steve8track on 2008-07-12
I would just open the System Monitor or htop, and kill the process that way, rather than running that rather big script.

Also, if you want a command to kill it, then try this:

```
killall npviewer.bin
```

You shouldn't need to run this command as root either.  This seems a lot simpler than using the command you were considering, and it worked for me.

If you are using Compiz Fusion, you could even put the above command in as a keyboard shortcut so you wouldn't have to type it out or use a console.  It can be used in either a terminal or in a text file run as a bash script.

I hope this helps.

Steve

---

### Post by doobydave on 2008-07-17
Could someone clarify whether this bug lies with Adobe or is it in the 64-bit wrapper?

It's starting to really bug me at present as I maintain a public computer in a cafe that also participates in Folding@Home. Npviewer.bin is often responsible for hogging my cores.

If it wasn't for ssh and top I would be pulling my hair out.


Is there a script that can automatically kill this cpu hog without any intervention?

---

### Post by NevilleDNZ on 2008-07-18
This program nices npviewer.bin and can even auto kill it after an hour of CPU is swallowed.

#!/bin/sh
help(){
more << erom
Name:
  nice_hog - run cpu hogs nicely (at a lower priority)

Usage:
  nice_hog -# [ /usr/lib/nspluginwrapper/npviewer.bin ] ...
  nice_hog --ulimit "ulimit options quoted" -# [ /usr/lib/nspluginwrapper/npviewer.bin ] ...
  nice_hog --unnice -# [ /usr/lib/nspluginwrapper/npviewer.bin ] ...
  nice_hog --help # this help text

Synopsis:
This tool(hack) was written to deal with the problem of rogue processes,
in particular $feral_list is the default.

This is achieved by adding "-1" to the name of the original program, and 
create a replacement that nices this renamed program.

You may also specify any of the ulimit options (in quotes) if you want
to further restrict the operation of the process.  An example would be
to kill the process after it uses an hours of CPU time, or if it's memory
usage gets to high.  See example 1 below.

The reason I wrote this program was because so many web pages have flash
embedded, and often when a flash ran on my laptop the CPU fan went nuts. I
mean "a web advertisement" chugging across the top of my screen, who
cares...  not me.  (Esp if it wastes watts, and makes green house gases)

Now if I could click on a tab in firefox and nice the hog pages forever
I would be a happy hacker.

Fortunately - on my laptop - when npviewer.bin is niced the CPU does
not scale up the MegaHertz, does not spin up the fan to full speed,
and does not make as much of a racket, and maybe it save your battery
from being suck dry.  (The flash does still suck a bit more power somehow)

Usage: (This will nice_hog npviewer.bin by default)
To install: (Only need to be root for system owned files)
# nice_hog /usr/lib/nspluginwrapper/npviewer.bin
OR
# nice_hog -5 /usr/lib/nspluginwrapper/npviewer.bin

To uninstall:
# nice_hog --unnice /usr/lib/nspluginwrapper/npviewer.bin

Example 1:
This example will raise the niceness to 2, and kill $feral_list if
it uses more the an hour of CPU...  Install as follows:
# nice_hog --ulimit "-t 3600" -2
-rwxr-xr-x 1 root root    268 2008-06-18 22:26 /usr/lib/nspluginwrapper/npviewer.bin
-rwxr-xr-x 1 root root 145692 2008-06-18 10:14 /usr/lib/nspluginwrapper/npviewer.bin-2
Note: killing you flash at 3600 might not be exactly what you want.
test it out with a shorter interval.

Example 2:
These commands work on almost any program (except /bin/sh), for example:

# nice_hog /usr/bin/xclock
-rwxr-xr-x 1 root root 62820 2008-04-05 04:22 /usr/bin/nice_xclock
-rwxr-xr-x 1 root root   168 2008-06-18 12:34 /usr/bin/xclock

# xclock -update 1 &
[28] 666

# ps -lp 666
F S   UID   PID  PPID  C PRI  NI ADDR SZ WCHAN  TTY          TIME CMD
0 S     0   666  555   0  81   1 -  2206 sys_po pts/3    00:00:00 xclock-1

# nice_hog --unnice /usr/bin/xclock
-rwxr-xr-x 1 root root 62820 2008-04-05 04:22 /usr/bin/xclock

Bugs^H^H^H^HFeatures:
The newly new script belongs to the person who created it (probably
root), and the permissions are a+rx (which may be not what you want).
Also on some systems renaming a file with the SetUI bit on may cause
the bit to be removed, or trigger a security audit alert.

The --ulimit option must appear first.

If the niceness isnt 1 you must also specify the niceness when unniceing.
# nice_hog --unnice -10 /usr/bin/xclock

Some error messages are not too helpful, esp from basename.

License: 
  GPL - Author NevilleDNZ
erom
}

feral_list="/usr/lib/nspluginwrapper/npviewer.bin" # etc ... (add your favourites)

if [ "$1" = "--help" ]; then
  help "$@"
  exit 1
elif [ "$1" = "--unnice" ]; then
  unnice="$1"; shift
fi

case "$1" in
  (--ulimit*)
    ulimit="ulimit $2"; 
  shift 2;;
esac

case "$1" in 
  (-[1-9]*)niceness="$1"; shift;;
  (+[1-9]*)niceness="$1"; shift;;
  (*)niceness="-1";; # just enough to prevent fan/AMD from warp speed
esac

if [ "$*" = "" ]; then
  set -- $feral_list
fi

domesticate(){
    cat << tac > "$feral"
#!/bin/sh
$ulimit
exec nice $niceness "$hog" "\$@"
#exec -a "$feral" nice $niceness "$hog" "\$@"
#exec -a "$basename" nice $niceness "$hog" "\$@"
tac
}

for feral in "$@"; do
  basename="$(basename "$feral")"
  hog="$(dirname "$feral")/$(basename "$feral")$niceness"
  if [ "$unnice" ]; then
    if [ -x "$hog" ]; then
      mv "$hog" "$feral"
    fi
    ls -l "$feral"
  elif [ ! -x "$hog" ]; then
    mv "$feral" "$hog"
    domesticate
    chmod a+rx "$feral"
    ls -l "$feral" "$hog"
  fi
done # od :guitar:

---

### Post by doobydave on 2008-07-19
Wow.

I'm sure that could be very useful.

---

