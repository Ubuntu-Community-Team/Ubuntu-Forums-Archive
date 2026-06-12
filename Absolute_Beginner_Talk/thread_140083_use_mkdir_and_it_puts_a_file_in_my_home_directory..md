---
title: "use mkdir and it puts a file in my home directory."
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by billh1241 on 2006-03-05
I am new of course.  I want to download Real player 10 and install it.  I did a terminal mkdir and it put a folder in my home directory.  I downloaded the file from real player. com and did every thing stated in the starter guide and it said the real player could not be found.  It did show my /home/bill/downloads file and when I did ls it showed the r p file there.
  Is there a book that explains all this stuff that I could read, I do not want to keep asking stupid questions here if I could find the answers  in a book written for non computer people.

Thanks, Bill

---

### Post by joshuapurcell on 2006-03-05
These aren't stupid questions. It would help to post the exact commands you have given so that we can better know what is needed to get the application to install/run. When you gave the **mkdir** command I'm assuming you followed that with the name of the folder you want to create like this:```
mkdir newFolder
```After it's created, you could then navigate into that folder:```
cd newFolder
```You can download whatever file you want and choose this new folder to save the file into (using your web browser). You will then have the file in the newly created folder, and you will have a terminal window opened and in the same location as the newly-downloaded file.

---

### Post by Mustard on 2006-03-05
It could be a case also of the filename you entered in the command being different from the name of the file in that folder.  Just thought I would add that possibility.

As mentioned above, if we could see what you were typing in and what the name of file is, and what folder it is in, then we would be closer to a solution.

Oh, and Bill, there are no stupid questions in the absolute begginers forum. :)  Ask anything you want.  You will get pointed towards lots of reading material along the way, believe me.

If you really want to have a read on terminal commands and finding your way around the terminal, here are some primers for you.

[http://ubuntuforums.org/showthread.php?t=45651](http://ubuntuforums.org/showthread.php?t=45651)
[http://www.linuxcommand.org/](http://www.linuxcommand.org/)
[http://ubuntuforums.org/showthread.php?t=73885](http://ubuntuforums.org/showthread.php?t=73885)

The search function in this forum is an excellent way of researching solutions to problems if you haven't tried it already.

---

### Post by billh1241 on 2006-03-05
Thanks for the help.  But, it did not work.
I wrote in Terminal   "mkdir new folder" it made the folder "new" in my home directory.  I did "cd new" and it did.  I downloaded the realplayer10gold.bin file in "new" wrote "chmod +x realplayer10gold.bin" and hit enter. Next I wrote "sudo ./realplayer10gold.bin" and it came back"./realplayer10gold.bin:error while loading shared libraries: libstdc++,so.5: cannot open shared object file: no such file or directory"

---

### Post by kaamos on 2006-03-05
Try again after this:
```
sudo apt-get install libstdc++5
```

---

### Post by billh1241 on 2006-03-05
I did that and after alot of screens go by I get "could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)

---

### Post by kaamos on 2006-03-05
1) make sure you used sudo

2) make sure you haven't got synaptic open in the same time

3) beats me. :(

---

### Post by billh1241 on 2006-03-05
Thanks, I went back and retyped all the entries and it worked...Thanks so much.  I am going to the sites on terminal and print out the instructions.

Thanks again,  Bill

---

