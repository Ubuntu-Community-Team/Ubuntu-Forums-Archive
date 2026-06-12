---
title: "Lost my privileges!"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by ageer1 on 2007-12-02
I just installed Gutsy over Feisty by erasing the root partition but preserving my home partition then installing. On bootup I couldn't login to my account so I started in recovery mode and added a new user with adduser using the same name and password. The new account doesn't have access to synaptic, add/remove, account control etc. Any help getting back to full control of my computer would be appreciated! Also what did I do wrong? Should I not have erased /root and allowed the installer to overwrite it?

Many thanks, Joe

---

### Post by irish_flu on 2007-12-02
your new user needs to be added to the "admin" group in order to have sudo privs, etc.

Boot back into the recovery console like you did before, and type:

adduser ageer1 -g admin

---

### Post by ageer1 on 2007-12-02
Thanks for the response, but didn't seem to take. I tried adduser esky -g admin rather than adduser ageer1 -g admin because i have a shitpot full of stuff in my "esky" home folder, could that be a problem?

---

### Post by hogwartsnigel on 2007-12-02
gksudo nautilus doesn't help in this instance does it? If it does could you not re-create amend the user files via this. I am probably way off as I am extremely new but this worked for me in several ways. Forgive me if it is of no use, just keen to start helping.

Nigel

---

### Post by bhold on 2007-12-02
Not sure about this but I wonder if when you deleted /, installed, then re-added your original user name maybe user ids and group ids of your original directory and file inodes got out of sync with contents of /etc/passwd and /etc/group files?

Suggest you  try this:

ls -l -n -d ~yourusername

For my system, this looks as follows:
bhold:~> ls -l -n -d ~bhold
drwxr-xr-x 60 1000 1000 4096 2007-12-02 15:35 /home/bhold

The first number (1000) right of the file count (60) is the user id. 

Next look in file /etc/passwd with your favorite editor, or just cat /etc/passwd. Find the entry for yourusername. For me, this entry looks as follows:
bhold:x:1000:1000:Brandt Holder,,,:/home/bhold:/bin/bash

The user id is the first numeric value right of the x:, 1000. So the inode user id value from the ls command matches the /etc/passwd user id and things are in sync. (I'm not sure what is up with this forum software, for some reason I have a face icon in my /etc/passwd entry. Sorry about that but you get the idea.)

Now, do the same thing and verify your group id values. Group id values are just to the right of the user id values - both 1000 in the above example.

---

### Post by ageer1 on 2007-12-02
Behold,
Thanks for the reply:
I get 
     drwxr-xr-x 73 esky esky 4096 2007-12-02 18:59 /home/esky
and
     esky:x:1000:1000:,,,:/home/esky:/bin/bash

No idea what this means, or if it's valuable information?? Not sure how I would change without admin privileges.
Thanks again,

Joe

---

### Post by bhold on 2007-12-02
ageer1, did you include the -n on your ls command? I do not see the numeric user id and group id values from the ls output. Please enter this command and post results.

ls -l -n -d ~esky

---

### Post by ageer1 on 2007-12-02
Yes, I input the command as written and got the indicated output.

In the meantime I've just finished reinstalling, using the same disk and the exact same procedure as before. The problem has evaporated, to both my surprise and consternation. Surprise because I did absolutly nothing different, and consternation because I'm forced to wonder if I will be facing these kinds of problems whenever I try to install an updated version of Ubuntu, which I enjoy using so much more than windows.

I really appreciate your attempts to help!!

Joe

---

