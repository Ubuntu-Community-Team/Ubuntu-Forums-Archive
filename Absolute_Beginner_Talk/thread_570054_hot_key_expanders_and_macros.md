---
title: "hot key expanders and macros"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by Alan Stancliff on 2007-10-07
I am a new user of Linux and Ubuntu, having been using Windows for years. I do a lot of production typing and editing. In Windows, I have been using several keyboard expanders and remappers. One such program is called [**_pcShorthand_**]("http://www.pcshorthand.com/"), another is called [**_Instant Text_**]("http://www.fitaly.com/overview/overviewpage.htm"), and the third is [Autohotkey.]("http://www.autohotkey.com/") (*all bolded underline text in this message are clickable links*)

Is there anything in Linux/Ubuntu that I can use that has similar functionality? I realize that a lot of Linux word processors have an autocorrect type function, but I'm looking for something a little broader.

One of the things I like about Autohotkey is that I have written a little script than remaps a few keys on my keyboard (a [**_Kinesis keyboard_**]("http://www.kinesis-ergo.com/keyboards.htm") with a  Dvorak layout) so that I can switch between Spanish and English. I remapped the [ key to be a hot key for accenting characters, and a double question mark (??) makes the upside-down question mark, whereas the double exclamation point (!!) makes the upside-down exclamation point.

---

### Post by Genecks on 2007-10-07
Xmacro and xbindkeys.

You'll most likely have to build xbindkeys if you want it to load a macro, which would have to be loaded from a script if I'm correct.
Newer versions of xbindkeys allow a person to launch scripts. Older versions don't allow that. Therefore, you'd have to use a newer xbindkeys.
I say script, because xbindkeys, for what I know, can't just launch a macro. To even launch a macro from the terminal, you have to use a bash command.
Thus, I say, put the command in a script. Then, bind keys or a key to the script, which would allow it to be launched.

Search the web, forum, and etc. for more information.

I don't suggest xnee, because it never worked for me. It worked in a different OS, which was Puppy Linux, but I couldn't get it to work in Ubuntu.
Some programs are really weird, but I know xmacro works in Ubuntu Feisty for now.

I don't think it will necessarily be as convenient as autohotkey, as I've worked in it myself. And there might be some kind of packages that allow the double exclamation mark, but I'm not sure of which ones. You might be able to tweak the keyboard settings in Linux, but I haven't played with those things yet. I've been meaning to mess with the Japanese and espanol settings, but I haven't.

These look good:
> # lenny (testing) (x11): Associate a combination of keys or mouse buttons with a shell command
1.8.2-1: alpha amd64 arm hppa i386 ia64 mips mipsel powerpc s390 sparc
# sid (unstable) (x11): Associate a combination of keys or mouse buttons with a shell command
1.8.2-1: alpha amd64 arm armel hppa hurd-i386 i386 ia64 kfreebsd-amd64 kfreebsd-i386 m68k mips mipsel powerpc s390 sparc 
[http://hocwp.free.fr/xbindkeys/xbindkeys.html](http://hocwp.free.fr/xbindkeys/xbindkeys.html) ---> [http://packages.debian.org/xbindkeys](http://packages.debian.org/xbindkeys)

Good luck.

---

### Post by peabody on 2008-02-18
I've got a program that does the hotstring stuff that autohotkey does.  The link is in my signature.  I'm looking for testers.

---

