---
title: "Linux Equivalent of Batch Files?"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by iMlazy on 2006-05-22
I'm playing around with my Ubuntu, and I'm wondering now if there is any corresponding file that is similiar to a DOS-batch file?

(Where I can just double click and it carries out a series of executions)

I've noticed that making files is rather odd with Linux but I'm still playing around ;)

---

### Post by aysiu on 2006-05-22
[QUOTE=iMlazy]I'm playing around with my Ubuntu, and I'm wondering now if there is any corresponding file that is similiar to a DOS-batch file?

(Where I can just double click and it carries out a series of executions)[/QUOTE] You mean like a shell script?

---

### Post by dmizer on 2006-05-22
your looking for bash scripts.

[http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html](http://www.tldp.org/HOWTO/Bash-Prog-Intro-HOWTO.html)

---

### Post by emarkay on 2006-10-16
Is that the only option?

First there's AUTOEXEC.BAT that does things on boot. (Deletes any index files and clears any temp and log files)
I presume GRUB handles that, correct?  If so or not, any suggestions?

Then, like XXXXXX.BAT, with a desktop icon, I have a Window$ program that clears temp files, printer cache, browser cookies, file cache, and URL history.  

What would I need to do to have a "clear all" icon on my GNOME desktop that I can write to do all the above (as needed ) with one mouse click??

Thank you!

---

### Post by ReaderRat on 2006-10-16
> **emarkay said:**
> 
What would I need to do to have a "clear all" icon on my GNOME desktop that I can write to do all the above (as needed ) with one mouse click??

Thank you!
You could use Firefox/Swiftfox (browser) with extensions, and it will do those things.

EDIT: Dump private data = CTRL+SHIFT+DEL

---

### Post by dmizer on 2006-10-16
> **emarkay said:**
> Is that the only option?

in windows, those are still just batch (.bat) files.  as far as programming goes, there's no difference between your clearing script and your autoexec.bat file.  much like there is no difference between your letter_to_mom.doc and report_for_boss.doc.

> What would I need to do to have a "clear all" icon on my GNOME desktop that I can write to do all the above (as needed ) with one mouse click??

writing a shell script to do the same thing as your XXXXXX.bat would be an extremely similar process to how you wrote it for windows.

but this really isn't necessary with firefox.  as ReaderRat pointed out all you have to do is click on: tools > clear private data ... and everything is cleared according to your preferences.  you can set this up in: edit > preferences > privacy tab > settings button (to choose what you want deleted).

---

### Post by emarkay on 2006-10-16
Right - I know all about Mozilla - being  Netscape used since floppies, but I use SeaMonkey (I loathe Firefox) and have the PrefBar extenson loaded, which clears out the browser (except for the location bar).  However, I also want to clear my download history, copy my bookmarks and address book to a backup directory, and a few other thigs.  When I get back to Window$, I will copy my batch files "over here" and see who can point me to a way so I can point and click to do my bidding.  Boo who hoo ha ha haaaa!  :)

---

### Post by rccharles on 2006-10-16
> **emarkay said:**
> Right - I know all about Mozilla - being  Netscape used since floppies, but I use SeaMonkey (I loathe Firefox) and have the PrefBar extenson loaded, which clears out the browser (except for the location bar).  However, I also want to clear my download history, copy my bookmarks and address book to a backup directory, and a few other thigs.  When I get back to Window$, I will copy my batch files "over here" and see who can point me to a way so I can point and click to do my bidding.  Boo who hoo ha ha haaaa!  :)

Perhaps you can share your profile between Linux and Windows with SeaMonkey.  You can with FireFox.


It is possible to share Your Firefox And Thunderbird Profiles Between Linux and Windows.  See this article: 
[http://forums.suselinuxsupport.de/index.php?showtopic=43116&pid=189772&st=0&](http://forums.suselinuxsupport.de/index.php?showtopic=43116&pid=189772&st=0&)

It is a general purpose Linux article, so do not worry about finding it in a Suse forum.


----

Bash is the default shell in Linux.  Look up how to write a bash script.

Robert

---

### Post by dmizer on 2006-10-17
> **emarkay said:**
> I will copy my batch files "over here" and see who can point me to a way so I can point and click to do my bidding.  Boo who hoo ha ha haaaa!  :)

perhaps i have not made myself clear.  shell scripting is not identical to batch scripting.  they merely provide a similar format for similar function.

ie:
batch scripting is to windows what shell scripting is to linux.

so you can't take a batch file and use it in linux, or even (as far as i know) convert it to be used in linux.  you'll have to learn the bash scripting language and rewrite them.

---

### Post by emarkay on 2006-10-17
No problem - I'll read up on shell scripts.

Thanks!

---

