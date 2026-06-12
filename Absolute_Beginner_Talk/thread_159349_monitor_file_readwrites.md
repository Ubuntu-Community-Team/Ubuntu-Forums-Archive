---
title: "monitor file read/writes"
date: 2006-04-12
forum: Absolute Beginner Talk
---

### Post by prophet on 2006-04-12
hello ubuntu user, can anyone tell me if there is a program to monitor read write access to files? I am new to linux and I've always found filemon from sysinternals to be very very useful for determining which files I need to modify permissions on or which file the program uses to save configuration settings.

Hope someone can help as I am currently very confused with the file system- things I need to find seem to be all over the place. While, it is true that in windows things are also scattered, at least usually I know where to look for the files I normally would need- everything in separate folder under program files. From my initial reading, things seems to be in logical places too in linux but everything is lumped together such that I see also things that I'm not supposed to touch or files from other applications in the same folder. Anyway, hope someone can help me find the program for easier administration.

I do like it very much and am not complaining as it is free. However, right now I don't think it can compete with windows yet in terms of usability.

---

### Post by prophet on 2006-04-12
forgot to add that I would prefer a kde app... thanks..

---

### Post by IYY on 2006-04-12
I'm not sure exactly what you mean. If you want to see the permissions on a file, just use ** ls -l <filename>** or** ls -l <directory>**.

If you want to check if a specific file is being currently written to or read from, use **lsof <filename>**

> I do like it very much and am not complaining as it is free. However, right now I don't think it can compete with windows yet in terms of usability.

It depends on how you define usability. For real novices, who just use the computer for e-mail and surfing the web, it's more usable than Windows because there is very little risk of malware. Most real experts (programmers, system administrators) will also say that it is more usable. I guess the people in the middle might have some trouble.

---

### Post by prophet on 2006-04-12
hello there... I do know how to see the permissions on a file both with the shell or the GUI. What I was looking for was a way to monitor which files a certain application is accessing so that I can for example prevent some users from modifying configuration files. Which implies that I'd also know where these configuration files are so I can modify them.. hope that was clear.. :) my english is not very good.

Just my opinion, I'm not exactly a novice with computers as I have been running xp as only limited account and totally locked down with ease (just by using filemon and regmon from sysinternals) -- I know some people say that it is impossible to work on xp with limited account but this is definitely not true as I have been doing it ever since it came out- without even looking at manuals if I may add- this is the degree of usability I meant. Only problem I can see is that windows is not secure by default, not to mention that it costs 100 or so bucks. This is why I am really hoping I can learn enough to make the complete switch.. Thanks again in advance

---

### Post by IYY on 2006-04-12
Well, the second command I mentioned checks which users/apps are accessing a particular file. If you want to see a list of all files currently open, the command is just **lsof**, with no args.

(By the way, you mentioned Filemon. I believe this particular app is avaliable for Linux.)

---

### Post by prophet on 2006-04-12
Thanks.. am using windows right now so I'll give it a try later... but just in case, will that work with piping to grep command so I can filter with application name I am running?>

---

### Post by prophet on 2006-04-12
also, if it lists all files currently open then it means it won't catch programs that do burst writes? meaning I can't leave it running then do a save on the configuration page of a program then see what file got accessed right? in that case, hope there is another alternative..:)

---

### Post by IYY on 2006-04-12
Sure, but even easier would be doing

lsof -c <commandname>

You could also look at dnotify (sudo apt-get install dnotify). It's a program that runs a command of your choice when the contents of a specific directory are changed.

---

### Post by prophet on 2006-04-12
what about burst writes? - previous post. or do all applications leave the config file open while I am looking at the GUI equivalent?

---

### Post by prophet on 2006-04-12
tried lsof. I don't think I can use this effectively for my purposes. Since some programs run so many files even if it keeps the config files open while I edit it, it would take too long to find out which one I need. Does anybody know of a better option, preferably one that can run in background while I'm working and recognize reads or writes.  This would make it easier since all I'll have to do then is to save the config file and watch for files that are being written to by a specific program. This was the functionality that filemon had. From what I read, the kernel was modified so that the version of that app for linux is now unusable.

---

### Post by prophet on 2006-04-12
will try dnotify tomorrow.. anyone has more suggestions please post here. thanks.

---

