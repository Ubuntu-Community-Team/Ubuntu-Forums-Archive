---
title: "New issue ( trying to run applications )- error"
date: 2006-10-10
forum: Absolute Beginner Talk
---

### Post by Ryupower on 2006-10-10
hi
after I installed the programs I now have a different issue, it won't execute! I get an error! 

this if I use the **GUI**: Details: Failed to execute child process "gaim" (No such file or directory)

**when I use the terminal**:gaim
bash: gaim: command not found


or by the other application ( terminal becasue I don't know where the program landed ):
$ licq
/usr/lib/licq/bin/licq-bin: error while loading shared libraries: libssl.so.4: cannot open shared object file: No such file or directory

What's wrong now??? Please help!

---

### Post by meng on 2006-10-10
Looking quickly over your previous posts, I have to ask: did you install these from source? from rpms? from debs?

Could be unmet dependencies, i.e. your programs are looking for other programs assumed to be on your system but which aren't. Would help to know exactly how you installed the programs, and why you didn't/couldn't do it using apt-get/aptitude/Synaptic (i.e. the "normal way")

---

### Post by bulldog on 2006-10-10
If you have installed GAIM2.0 I think there's something not entirely right.:D 

Try to use the following HowTo and see if that works.[it does for me]

[http://ubuntuforums.org/showthread.php?t=204523](http://ubuntuforums.org/showthread.php?t=204523)

---

### Post by Ryupower on 2006-10-10
> **meng said:**
> Looking quickly over your previous posts, I have to ask: did you install these from source? from rpms? from debs?

Could be unmet dependencies, i.e. your programs are looking for other programs assumed to be on your system but which aren't. Would help to know exactly how you installed the programs, and why you didn't/couldn't do it using apt-get/aptitude/Synaptic (i.e. the "normal way")

one's a .deb package and the other is a .rpm package which was turned into a .deb package.
for both I used the "sudo dpkg -i" command.

note: I just looked,it turned out that one was broken ( now fixed, gaim ) the other says it's installed ( got a green mark,licq ) but when I run the command "licq" I get the above message. why?

---

### Post by meng on 2006-10-10
Wouldn't it have been easier to install using apt-get/aptitude/Synaptic? (would need to have universe repositories enabled) Then dependencies would have been satisfied automatically. You can't expect every .deb to work specifically with Ubuntu (unless specifically created for Ubuntu, and even then sometimes it doesn't), and as for converting rpms, that's even more likely to go bad for you.

---

### Post by Ryupower on 2006-10-10
> **meng said:**
> Wouldn't it have been easier to install using apt-get/aptitude/Synaptic? (would need to have universe repositories enabled) Then dependencies would have been satisfied automatically. You can't expect every .deb to work specifically with Ubuntu (unless specifically created for Ubuntu, and even then sometimes it doesn't), and as for converting rpms, that's even more likely to go bad for you.
I'll try that, but first I need to know how to enable universe repositories in the "hoary hedgehog" release. Can someone tell me please? 
Also, when downloading a package, must I usually also download the others around it ( the ones ending with the same ending or the ones in the same section)?

alternative question: how do I upgrade w/h CD?

Sorry about me being such a newbie. :/

---

