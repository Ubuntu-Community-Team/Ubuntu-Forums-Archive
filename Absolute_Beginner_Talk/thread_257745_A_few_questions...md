---
title: "A few questions.."
date: 2006-09-14
forum: Absolute Beginner Talk
---

### Post by MrLeN on 2006-09-14
1). How do I set a specific browser as default? I installed a new browser, but it has become the default. I want the old (FireFox) one as default.

2). How can I set a file type to open with a certain program? I know that I can right click and "open with".. but how can I set that permanently?

3). I have an External HDD, but I am unable to save files into it via uBuntu. When I try it says that it does not have write permissions. So I check permissions in properties, and tick "write" but I get a message saying "Could't Change the permission of External USB because it is a read only disk"; note: I named the drive "External USB" from Windows. I really need this drive and I need to be able to write to it, because I want to keep all my stuff there so I can get to it from Windows and Ubuntu -- depending on what I am using.

Any help appreciated.

MrLeN

**Edit:** Oh, and how to I set a program to start up automatically when Ubunto starts up (like the Windows startup folder). I asked someone before, and I was told how, but I can't find the thread. Sorry.

---

### Post by mokmoki on 2006-09-15
1.) not sure how, i've been using ubuntu for less than a week

2.) i'm not sure with the general solution for this, but what i did in my case (i was making realplayer the default for .rmvb), i right click -> properties then "open with" tab, then there was a list of programs, and there were radio buttons beside the programs. i just selected the radio for realplayer, then selected Ok, then it became my default.

3.) i also have an external HDD. the reason you aren't able to write to it is because linux uses a different file system from windows. linux cannot write to NTFS file systems (a perfect solution hasn't been made yet), but it can read from it. so the most you can do is read from your HDD. There are some **experimental** (use at your own risk) ways of making Ubuntu able to write to NTFS, but I still haven't tried them since they're still experimental.

4.) try going to System -> Session then choose the tab "Startup Programs". from there you can type the command that you want Ubuntu to execute at boot time.

Hope this helps, but the experts can answer your questions better. I just started using Linux last week...

---

### Post by jmwhokie on 2006-09-15
on #1) Your System->Preferences->Preferred Applications will do the trick.

---

### Post by Wolki on 2006-09-15
> **MrLeN said:**
> 1). How do I set a specific browser as default? I installed a new browser, but it has become the default. I want the old (FireFox) one as default.


System -> Preferences -> Preferred Applications

> 2). How can I set a file type to open with a certain program? I know that I can right click and "open with".. but how can I set that permanently?

Right-click, Preferences, Open with tab, set the radio button to the application you selected.

> I have an External HDD, but I am unable to save files into it via uBuntu. When I try it says that it does not have write permissions. So I check permissions in properties, and tick "write" but I get a message saying "Could't Change the permission of External USB because it is a read only disk"; note: I named the drive "External USB" from Windows. I really need this drive and I need to be able to write to it, because I want to keep all my stuff there so I can get to it from Windows and Ubuntu -- depending on what I am using.


If you have it formatted as NTFS, you're out of luck currently - The drivers for read/write support are being worked on for quite some time now, and we'll likely see support within the next year I hear, but currently it's still experimantel and you risk losing data. With FAT there's no problem.

> Oh, and how to I set a program to start up automatically when Ubunto starts up (like the Windows startup folder). I asked someone before, and I was told how, but I can't find the thread. Sorry.

Either use the sessions manager (System -> Preferences -> Sessions), or drag from the menu into the hidden folder .config/autostart

---

### Post by MrLeN on 2006-09-15
Fantastic -- Thanks Guys.

I can reformat the external HDD, no problem. I'll just go to Windows, put the files somewhere else temporarily and reformat it. What should I reformat it as?

MrLeN

---

### Post by wvslkr on 2006-09-15
You can format as fat32 or ext3fs. Fat32 has a 4g file size limit. There is 
driver for win that allows it to read and write e3fs.  Can't recall the exact name off the top right now.  Sure someone will jump in or I'll look it up later if needed.

---

### Post by MrLeN on 2006-09-15
I reformatted it as Fat32 and now it works fine. Excellent, thank you very much.

MrLeN

---

