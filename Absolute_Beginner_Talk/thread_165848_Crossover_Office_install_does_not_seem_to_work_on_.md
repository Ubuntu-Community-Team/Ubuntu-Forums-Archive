---
title: "Crossover Office install does not seem to work on my Ubuntu 5.10"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by 1002285 on 2006-04-25
I downloaded Crossover Office trial version in order to use MS Word (I know OpenOffice can't correctly  handle the file I need to work on).
After the command sh filename.sh I can't find Crossover in my applications menu, although the installation instructions say that after that it should be installed. And I don't see any answer in the terminal window either.
Can anybody guess what the problem could be?

---

### Post by khightower on 2006-04-25
[QUOTE=1002285]I downloaded Crossover Office trial version in order to use MS Word (I know OpenOffice can't correctly  handle the file I need to work on).
After the command sh filename.sh I can't find Crossover in my applications menu, although the installation instructions say that after that it should be installed. And I don't see any answer in the terminal window either.
Can anybody guess what the problem could be?[/QUOTE]

Just want to know, what was it about your word doc that open office writer could not do. 

I just want to know, because I switch alot of Business clients over to Open Office. It would be nice to have a heads up on some Word-to-Writer issues

---

### Post by 1002285 on 2006-04-25
I have a file to translate where all paragraphs have numbers and there are often references made in the text to other paragraphs (like "(see paragraphs ...-...)" and clicking on these references gets you to the referred paragraph).
I had a same kind of file a couple of weeks ago and I translated it with OpenOffice.org (probably 2.0, not 2.0.2) and realized only later that it had not understood the numbering and references of the MS Word file correctly, so I had to put in about another hour to work it out in MS Word. I did it all on Windows and now I need to get working on a same kind of text with numbering and references, but the computer that I normally use and that runs Windows, is in the shop, so I thought I will see whether this can be done on a Linux system.
I haven't actually started trying the file in OOo on this Ubuntu yet, I have spent a lot of time on getting the system to work, but am hoping to get to it - perhaps first on OOo, just in case - and then with Crossover and MS Office.

---

### Post by khightower on 2006-04-25
[QUOTE=1002285]I have a file to translate where all paragraphs have numbers and there are often references made in the text to other paragraphs (like "(see paragraphs ...-...)" and clicking on these references gets you to the referred paragraph).
I had a same kind of file a couple of weeks ago and I translated it with OpenOffice.org (probably 2.0, not 2.0.2) and realized only later that it had not understood the numbering and references of the MS Word file correctly, so I had to put in about another hour to work it out in MS Word. I did it all on Windows and now I need to get working on a same kind of text with numbering and references, but the computer that I normally use and that runs Windows, is in the shop, so I thought I will see whether this can be done on a Linux system.
I haven't actually started trying the file in OOo on this Ubuntu yet, I have spent a lot of time on getting the system to work, but am hoping to get to it - perhaps first on OOo, just in case - and then with Crossover and MS Office.[/QUOTE]

Thanks. I had a few clients that had trouble with 00.o as well. Most issues were dealing with how to do things that they use to do in MS Office in 00.o

I hope you find a solution. Sometimes my clients had to redo a document and save it in a open format. That way they did not get stuck with having to use only MS office in the future.

---

### Post by Perfect Storm on 2006-04-25
Try first with
```
killall gnome-panel
```
and see if it appears.

---

### Post by 1002285 on 2006-04-25
Hmm,
the point of "killall" was to quit all programs?
I tried it and got:
gnome: no process killed
panel: no process killed
and I still don't see crossover anywhere

---

### Post by Perfect Storm on 2006-04-25
Which version(warty,hoary,breezy,dapper) of ubuntu do you use, and what Desktop Enviroment do you use (KDE, Gnome, Xfce etc)

---

### Post by nalmeth on 2006-04-25
It should have installed a CXOFFICE folder in your /home
KDE has a Crossover Menu entry for me, and Gnome doesn't..

---

### Post by Perfect Storm on 2006-04-25
Strange...I have both in breezy and dapper (gnome) with Crossover-office.
Tried with the editor to activate the tab menu? Try with the latest menu editor (0.8 ) for breezy  : [http://ubuntuforums.org/showthread.php?t=82537](http://ubuntuforums.org/showthread.php?t=82537)
and dapper (0.9): [http://ubuntuforums.org/showthread.php?t=163272](http://ubuntuforums.org/showthread.php?t=163272)

---

### Post by 1002285 on 2006-04-26
Thanks for trying to answer.
I have Breezy, 5.10, and only Gnome desktop.
I cannot keep trying right now, but I guess that maybe it did not install at all.
Is the command that I use at least right? sudo sh install-crossover-standard-demo-5.0.1.sh (and yes - I dit it being in the right folder)
After this command the terminal just asks for password and then gives no other reaction.

---

### Post by Perfect Storm on 2006-04-26
It should display something while running the script and you are doing it correctly. Maybe a borked download of the script file?

---

### Post by 1002285 on 2006-04-27
OK thank you, archive integrity was a problem there, I downloaded the file again and then it started installing.
But after several lines of dots a new application window "Crossover Office Standard Setup" opened and gave this message:
""(dollar sign)HOME" must exist and belong to you in order for the installation to proceed. You may need to login as root or use su rather than sudo".
I tried again, using su - this gave some kind of error message about "su".
Then I logged in as a root using "sudo -s", which made the line start with "root@Dell:" and tried installing again using
"sh install-crossover-standard-demo-5.0.1.sh"
"sudo sh install-crossover-standard-demo-5.0.1.sh"
and got the same answer both times.
I tried creating that folder and got the answer that "... file exists". So why would there be a problem of owning this folder even after logging in as root?
(As you can see, keypad is another big problem for me - I can't use dollar sign and any other ctrl-alt-combinations I know from Windows - they do something else here even now that I have got teh system to work with Estonian layout.)

---

### Post by 1002285 on 2006-04-27
OK thank you, archive integrity was a problem there, I downloaded the file again and then it started installing.
But after several lines of dots a new application window "Crossover Office Standard Setup" opened and gave this message:
""(dollar sign)HOME" must exist and belong to you in order for the installation to proceed. You may need to login as root or use su rather than sudo".
I tried again, using su - this gave some kind of error message about "su".
Then I logged in as a root using "sudo -s", which made the line start with "root@Dell:" and tried installing again using
"sh install-crossover-standard-demo-5.0.1.sh"
"sudo sh install-crossover-standard-demo-5.0.1.sh"
and got the same answer both times.
I tried creating that folder and got the answer that "... file exists". So why would there be a problem of owning this folder even after logging in as root?
(As you can see, keypad is another big problem for me - I can't use dollar sign and any other ctrl-alt-combinations I know from Windows - they do something else here even now that I have got teh system to work with Estonian layout.)

---

