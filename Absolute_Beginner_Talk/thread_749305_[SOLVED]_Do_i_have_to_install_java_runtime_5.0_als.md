---
title: "[SOLVED] Do i have to install java runtime 5.0 also?"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by diplomat.x on 2008-04-08
[IMG]http://img223.imageshack.us/img223/3989/81158009ph7.jpg[/IMG]


Sometimes Java works in my system and sometimes it dont. And when it doesnt, even restarting PC n number of times doesnt help. 

I am using firefox and have just downloaded Opera. But looks like i need to specify in options of opera about the java directory location...but i dont know where it is?
And i was reading other threads where people are telling others to delete /home/username/.mozilla folder, but i dont have any folder like that? :(

I was just wondering if installing runtime 5.0 would solve this issue? :confused:

---

### Post by SpongeBob SquarePants on 2008-04-08
> **diplomat.x said:**
> And i was reading other threads where people are telling others to delete /home/username/.mozilla folder, but i dont have any folder like that? :(:

The .mozilla folder is a hidden folder. Are you sure you don't have it? Look in your Home folder and if it's not there hit "view" up on the bar and tick "show hidden files". You should be able to see it after that.

---

### Post by gandaran on 2008-04-08
> **diplomat.x said:**
> [IMG]http://img223.imageshack.us/img223/3989/81158009ph7.jpg[/IMG]


Sometimes Java works in my system and sometimes it dont. And when it doesnt, even restarting PC n number of times doesnt help. 

I am using firefox and have just downloaded Opera. But looks like i need to specify in options of opera about the java directory location...but i dont know where it is?
And i was reading other threads where people are telling others to delete /home/username/.mozilla folder, but i dont have any folder like that? :(

I was just wondering if installing runtime 5.0 would solve this issue? :confused:

no, sun-java6 is the latest java, should work every time, for firefox just check in synaptic if sun-java6-plugin is installed, for opera you'll have to find the path to java (opera » tools » preferences » advanced » content » java options) try this one  /usr/lib/jvm/java-6-sun/jre/lib/i386 and click the validate button.

---

### Post by diplomat.x on 2008-04-08
@ Sponge Bob.

Thank u very much, i can now see the hidden files. I just deleted .mozilla folder and java is working fine as of now.

@ gandaran

Thanks a lot to u too, i was successfully able to get java working in opera after adding the link in the options.

Many thanks to both of u again.

---

