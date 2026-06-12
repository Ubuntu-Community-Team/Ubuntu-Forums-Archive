---
title: "Matlab File Permissions"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by biomechmike on 2008-04-16
I've just installed Matlab R2008a. It frequently displays the message "The desktop configuration was not saved successfully" when the focus of the window, among other things.

I believe it is because the program does not have write access to where it is installed (/usr/local/matlabR2008a).

This problem also prevents the path from being set from the file menu.

Is there a way for me to allow Matlab to have the appropriate permissions? Is it a bad idea to let it?

Thanks,

Mike

---

### Post by hums07 on 2008-04-16
> **biomechmike said:**
> 
I believe it is because the program does not have write access to where it is installed (/usr/local/matlabR2008a).

This problem also prevents the path from being set from the file menu.

Is there a way for me to allow Matlab to have the appropriate permissions? Is it a bad idea to let it?

I dont think it is a bad idea at all, because afaik /usr/local/ is reserved to something being local (local computer/user) so it wont affect the way the system works.
You can try to change the permission so that all can write to the directory (and its subs):
```
sudo chmod a+w -R /usr/local/MatlabR2008a
```

---

### Post by biomechmike on 2008-04-16
Thanks for the fix.

I was actually wrong about what folder needed the permission changed...

It was /home/usr/.matlab/R2008a.

Thanks again.

---

### Post by Dionysios on 2008-04-30
In my computer, the problem persists, I have changed the permissions but still I get this message every time. When matlab starts, it displays this message twice, and if I dont do anything, it keeps printing it, one line every ten seconds or so.
Any ideas?

Thanks in advance!

---

### Post by blindwidow on 2008-05-25
> **Dionysios said:**
> In my computer, the problem persists, I have changed the permissions but still I get this message every time. When matlab starts, it displays this message twice, and if I dont do anything, it keeps printing it, one line every ten seconds or so.
Any ideas?

Thanks in advance!

You should apply the advice of biomechmike. Type 
sudo chmod a+w -R /home/usr/.matlab/R2008 where usr is you user name. I was having the same problem. Now it's solved.

Have a nice day everyone...

---

### Post by ene_dene on 2008-05-25
> **Dionysios said:**
> In my computer, the problem persists, I have changed the permissions but still I get this message every time. When matlab starts, it displays this message twice, and if I dont do anything, it keeps printing it, one line every ten seconds or so.
Any ideas?

Thanks in advance!
Go from file to file, directory to directory and change permissions so that you are the owner and it'll work I mean in /home/you/.matlab

---

### Post by adi_8079 on 2008-06-05
It worked for me, thanks guys!

---

### Post by curiousmonk on 2008-06-10
Worked for me!  Matlab R2008a on Ubuntu 8.04.

sudo chmod a+w -R /home/$USER/.matlab

Thanks!

---

### Post by p-k on 2008-06-29
I think it's better to change not a write permission, but the owner. like ene_dene has written above:

```
sudo chown -R USERNAME:USERNAME ~/.matlab
```
where the _second_ USERNAME is actually a groupe name (in Ubuntu only you're the member of it)

---

