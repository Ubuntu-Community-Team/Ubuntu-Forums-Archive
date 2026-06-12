---
title: "Set max trash size in Kubuntu?"
date: 2007-09-30
forum: Absolute Beginner Talk
---

### Post by Shadow ZERO on 2007-09-30
I'm having trouble locating any type of trash can settings in Kubuntu.  I really need to figure out how to limit my trash can size.

Side Note: It seems like any time i have a very basic beginner question, this forums search feature doesn't ever find anything.  I'm sure its been answered a thousand times before, but i can't figure out how to manipulate the search feature of these forums for a damn.  Oddly enough however advanced questions with very specific answers usually find good results, its only the simple and obvious questions that i have problems finding on these forums.

Also, the actual "Search" feature on the main menu never finds anything good.  Instead of that, i have to go to "Make New Topic"  Type a subject, and let the automatic similar threads suggestion find me results.  I hate making threads that ask questions that i know have been answered dozens of times(as i'm doing now), but until the search feature gets revamped to work like it does on most other forums, i will continue to do so with impunity.

---

### Post by kerry_s on 2007-09-30
i don't think you can. but if you really wanted to force it i believe you can try to force the trash folder to a set size. i'm sure you'll get some kind of problems though.

why do you need to limit it?

---

### Post by Shadow ZERO on 2007-09-30
Convenience really.  I delete a lot of stuff, sometimes very big files, and I want to know that no huge amount of my drive is being used up without having to check all the time.

Anyway, here's another thread i've found that has a potential solution, but its beyond my understanding as of yet.  Maybe someone can help me interpret this method.

[http://ubuntuforums.org/showthread.php?t=319211](http://ubuntuforums.org/showthread.php?t=319211)

This thread talks about writing a script, and putting it in your cron.hourly(daily, weekly, whatever) folder.  Here's the code for the one i liked:

```
[ $(du -sm /home/rcw/.Trash/|awk '{print $1}') -gt 800 ] && rm `ls -tald /home/rcw/.Trash/* |tail -1|head -1 |awk '{print $8}'`
```

If i wanted to use this method, would i simply copy/paste this info into a plain text file, and put that file in the cron.* folder?  does the file have to adhere to a naming syntax?

Thx for help :)

---

### Post by kerry_s on 2007-10-01
interesting, you'll have to make some changes to the script for it to work for you.

"/home/rcw/.Trash/" <these section's will have to be changed to your setup

"rcw" will be your login name
".Trash" you'll need to put the path to your trash folder, so you'll want to find that, if that's all good you'll be good to go.

just
```
kdesu kwrite /etc/cron.hourly/trash
```
put
```
#!/bin/sh
[ $(du -sm /home/your-name/.Trash/|awk '{print $1}') -gt 800 ] && rm `ls -tald /home/your-name/.Trash/* |tail -1|head -1 |awk '{print $8}'`

```

make it executable:
```
sudo chmod +x /etc/cron.hourly/trash
```

hope i got that right. :)

---

