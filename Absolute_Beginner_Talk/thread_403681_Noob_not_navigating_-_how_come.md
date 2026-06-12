---
title: "Noob not navigating - how come"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by flyer23 on 2007-04-07
Hi guys,

I can't seem to navigate to directories I know for a fact are there.  I created a directory called /home/test/ wtih the mkdir command and I can easily get there. No problem just do the cd /home/test and I'm there.

I made a directory called home/tim/ with the file browser and then created a subdirectory called home/tim/dowloads.  Both are showing in file browser, but I can't navigate to either one of them via command line?  

How come I can hit a directory I made with the line editor, but not ones created with fiile browser?  I must be missing something super easy.  Checked and rechecked I have the names exactly as they are. So it is not a mistype I promise. Here is the usual output:

tim@tim-desktop:~$ cd /home/tim/downloads
bash: cd: /home/tim/downloads: No such file or directory

Sorry to go this basic gang, but what am I missing?

---

### Post by Hieronymus on 2007-04-07
sounds odd, can you post the output of an ls -l done from you home folder? 

```

cd /home
ls -l

```Jeroen

---

### Post by flyer23 on 2007-04-07
Thanks.  Here is what I get

drwxr-xr-x  2 root root 4096 2007-04-06 23:32 test
drwxr-xr-x 32 tim  tim  4096 2007-04-07 11:15 tim

---

### Post by Hieronymus on 2007-04-07
try to do this:

```

cd /home
sudo chown tim ./test && sudo chgrp tim ./test

```

and try again to approach  the dir from the browser.

Jeroen

---

### Post by flyer23 on 2007-04-07
well the command line entry just sends me back to:

tim@tim-desktop:/home$

So the situation now is I can see the test directory in both the command line and the browser, but 

I still can't get to cd /home/tim/  which is still looking me right in the face in the browser. 

Weird thing is when I look at the blue folder that is in the home directory called tim there is a white house icon sitting side the tim folder icon . . . there is no little while house on the test folder that I can get in

Weird.

---

### Post by Hieronymus on 2007-04-07
> **flyer23 said:**
> well the command line entry just sends me back to:

tim@tim-desktop:/home$

So the situation now is I can see the test directory in both the command line and the browser, but 

I still can't get to cd /home/tim/  which is still looking me right in the face in the browser. 

Weird thing is when I look at the blue folder that is in the home directory called tim there is a white house icon sitting side the tim folder icon . . . there is no little while house on the test folder that I can get in

Weird.

The reason you see the white house is that for the user Tim this folder is seen as the home folder. Although it isn't physically. But back to the problem, when you do ls -l you must now see that the test folder is both owned and by tim and that the group is also tim. 
When you do the following, can you reach the folder then?

```

su
cd /home/test

```

jeroen

---

### Post by flyer23 on 2007-04-07
yes with the last command set I can get into the /home/test folder no problem.

different story with the /home/tim/

Still can't get to that one with the command line by going either:

tim@tim-desktop:/home$ cd /tim
bash: cd: /tim: No such file or directory
tim@tim-desktop:/home$ cd /home/tim/
tim@tim-desktop:~$ cd /tim
bash: cd: /tim: No such file or directory

No command line combo with the cd command will get me to the /home/tim/ directory.    

BTW thanks for taking time on your Saturday for the help . . . most appreciated.

---

### Post by Hieronymus on 2007-04-07
ok, found the problem

you try to get to the folder /tim instead of  /home/tim
If you give the command cd  /tim the system searches for tim in the root. If you are already in the home folder you must do cd tim or cd ./tim

Jeroen

PS. No problem, my girlfriend is playing a football match anyway so I've got the time.

---

### Post by flyer23 on 2007-04-07
Okay I tried the command as you provided both ways inside the /home directory and when I type 

tim@tim-desktop:~$ cd /home/
tim@tim-desktop:/home$ cd tim
tim@tim-desktop:~$

tim@tim-desktop:/home$ cd ./tim
tim@tim-desktop:~$

Just loops me back to the desktop command line when it should be dropping right into /home/tim

It is like the command just isn't registering, but I get no error . . . just loops me back to desktop line.

---

### Post by Hieronymus on 2007-04-07
hmm, I see, indeed it wasn't the problem because also in your earlier post you did cd /home/tim and this is correct. I shall make a folder on my system and try to do the same, then I post it here so please check if every step you do is the same. 

```

jeroen@laptop:/$ cd home
jeroen@laptop:/home$ sudo mkdir ./test
jeroen@laptop:/home$ ls -l
total 1
drwxr-xr-x 22 jeroen jeroen 1080 2007-04-07 19:05 jeroen
drwxr-xr-x  2 root   root     48 2007-04-07 20:09 test
jeroen@laptop:/home$ sudo chown jeroen ./test/ && sudo chgrp users ./test/
jeroen@laptop:/home$ ls -l
total 1
drwxr-xr-x 22 jeroen jeroen 1080 2007-04-07 19:05 jeroen
drwxr-xr-x  2 jeroen users    48 2007-04-07 20:09 test
jeroen@laptop:/home$ cd test/
jeroen@laptop:/home/test$ ls
jeroen@laptop:/home/test$ 

```

See anything different?
Does the same problem exist when doing all this as root?

Jeroen

---

### Post by Hieronymus on 2007-04-07
STOPSTOPSTOP

There is no problem, you are in your tim folder. the ~ sign tells you that you are in the users home folder. Try to do a ls when in this folder, you'll see. 

(I really need some coffee, hopefully this time I am right indeed :-) )

Jeroen

---

### Post by Maestro23 on 2007-04-07
> pwd

Just FYI: Tells you were you are at.

---

### Post by flyer23 on 2007-04-07
Yes it has me showing exactly what your showed.  It even leaves me at:

tim@tim-desktop:/home$ cd ./test
tim@tim-desktop:/home/test$

That works like a charm.  But still can't access the /home/tim folder.  So here is what I am thinking . . . since all the the folders I created the other day with file browser seem to be the offending parties . . . I'm just going to do the mkdir command and move the contents in the newly created folders?  Because now I can jet into /home/test/ without difficulty.  Guessing for some reason the ealier created directories got corrupt somehow.   So I'm thinking we've got it solved what do you think?

---

### Post by Hieronymus on 2007-04-07
did you read my last reply? I think there never was a problem, we just were not aware of the way some things are shown in the cli. 

Jeroen

---

### Post by flyer23 on 2007-04-07
You are absolutely right that was it!!!  And the pwd command proved it.  Jeez talk about noob pilot error.  Well I can tell you I learned a lot and sincerely thanks for all the time.  You help saved me from what I thought would have to be a reinstall but turned out I wasn't aware of where I was.

No wonder I couldn't get to the directories and unpack any of the tar files.  I was not where I thought I was.

Thanks again Hieronymus -  the Ubuntu community really is as great as everyone says.

---

### Post by Hieronymus on 2007-04-07
No problem, enjoy your stay and don't hesitate to post you questions.

Jeroen

---

