---
title: "How do you recursively delete a specific file type?"
date: 2006-07-14
forum: Absolute Beginner Talk
---

### Post by PhilOSparta on 2006-07-14
I have a lot of .LCK files in sub directories.  What terminal command will permit me to delete all of them?

I can list all of them using:  ls -lR | grep ".LCK"
Now I want to delete them.
I tried rm -R *.LCK  but that doesn't work.
The man pages for rm seem to indicate that rm is only used to remove files in the working directory OR the entire directory and/or all sub directories.
I only want to remove all .LCK files in all sub-directories of the working directory.

Thanks,
Phil

---

### Post by croak77 on 2006-07-14
find . -type f -name "*.LCK" -exec rm -f {} \;   

If you want confirmation:

find . -type f -name "*.LCK" -exec rm -i {} \;

---

### Post by jayemef on 2006-07-14
In bash you could use
```
$ find -name '*.LCK' -print | xargs rm
```

Or if you happen to use zsh, you could use
```
$ rm **/*.LCK
```

---

### Post by PhilOSparta on 2006-07-14
Close, but no cigar!

croak77
> find . -type f -name "*.LCK" -exec rm -f {} \; 

EDIT:  This worked, but watch the spacing.  It didn't work until I actually cut and pasted it.

The **find . -type f -name "*.LCK"** yielded a nice listing.

jayemef
> $ find -name '*.LCK' -print | xargs rm
Yielded:   rm: missing operand

EDIT: After one day on the forum, this thread has additional good ideas.
Although the above entry by croak77 worked, there may be a better approach for you.  Read on!
Thanks.

---

### Post by croak77 on 2006-07-14
> **PhilOSparta said:**
> Close, but no cigar!

croak77

This yielded:   bash: -exec: command not found

Although the find . -type f -name "*.LCK" yielded a nice listing.



It works for me. Maybe you there was a type-o or something. With confirmation.

```
find . -type f -name "*.LCK" -exec rm -i {} \;
```

or without confirmation

```
find . -type f -name "*.LCK" -exec rm -f {} \;
```

---

### Post by jayemef on 2006-07-14
Thats odd, because it definitely worked for me:

---

### Post by dasunst3r on 2006-07-14
Try *rm -rf *.lck*

As a precaution, you should *cd* into the directory you are working with.

---

### Post by jayemef on 2006-07-14
> **PhilOSparta said:**
> I tried rm -R *.LCK  but that doesn't work.
The man pages for rm seem to indicate that rm is only used to remove files in the working directory OR the entire directory and/or all sub directories.
He already tried it -- didn't work.

---

### Post by aysiu on 2006-07-14
How about using *gnome-search-tool* to find ```
*.LCK
``` and then just highlight them all and delete them that way?

---

### Post by croak77 on 2006-07-14
> **aysiu said:**
> How about using *gnome-search-tool* to find ```
*.LCK
``` and then just highlight them all and delete them that way?

Cause CLI > GUI :D

---

### Post by aysiu on 2006-07-14
> **croak77 said:**
> Cause CLI > GUI :D
No, because you should always find the right tool for the job, and given that after seven responses, there's no working CLI command, I think GUI is the right tool for *this* job.

There are plenty of tasks for which CLI is better--downloading an entire webpage, changing the image format on 400 images, installing 30 different packages from the repositories...

---

### Post by jayemef on 2006-07-14
Actually he was able to get it working, and out of those 7 replies, I believe all of them work (other than the one I had commented on). He just missed a space.

However, I would agree that for a user not adept with the command line, your solution is pretty solid.

---

### Post by croak77 on 2006-07-15
> **aysiu said:**
> No, because you should always find the right tool for the job, and given that after seven responses, there's no working CLI command

The poster asked for a terminal command. My original reply worked, try it for yourself. And not everyone wants or has gnome-search-tool installed.

---

### Post by aysiu on 2006-07-15
> **croak77 said:**
> The poster asked for a terminal command. My original reply worked, try it for yourself. And not everyone wants or has gnome-search-tool installed.
"What terminal command...?" is very different from "I know this can be done from the GUI, but I want to learn the terminal command for this."

---

### Post by croak77 on 2006-07-15
> **aysiu said:**
> "What terminal command...?" is very different from "I know this can be done from the GUI, but I want to learn the terminal command for this."

Yes but the poster asked for a terminal command and followed it up by posting the commands he/she had tried. I assumed the poster wanted a terminal command. Maybe my assuption is wrong. I don't know. I just thought I was being helpful.

---

### Post by aysiu on 2006-07-15
> **croak77 said:**
> Yes but the poster asked for a terminal command and followed it up by posting the commands he/she had tried. I assumed the poster wanted a terminal command. Maybe my assuption is wrong. I don't know. I just thought I was being helpful.
You were being helpful. I just tacked on something else I guess wasn't needed. No point in arguing about it now. OP's happy. We should be too.

---

