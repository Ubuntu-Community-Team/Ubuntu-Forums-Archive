---
title: "How do get rid of a virus"
date: 2006-02-10
forum: Absolute Beginner Talk
---

### Post by kent41 on 2006-02-10
I have just installed Clamav  and run it and Clamav shows i have 4 viruses.

However Clamav does not list the file names or directory they are located in.

the question is how do i find the virus to delete them.

Thanks
 Kent41

---

### Post by rado_london on 2006-02-10
I dont use any antivirus but I am amazed that you have viruses. How did you manage to get them?:D

---

### Post by kent41 on 2006-02-10
They just showed up when i ran Clamav in the Clamav summary.

Maybe you have viruses and don't know it.

---

### Post by Perfect Storm on 2006-02-10
It's windows virus's it won't affect your linux. But would be good idea to get rid off it so they don't pass to a win user.

---

### Post by Mustard on 2006-02-10
If you type this in terminal you should be able to see the manual for clamscan..

```
man clamscan
#hit the 'q' key to exit the manual
```

I've just been reading over it, and I'm not yet sure how you would proceed.  There is an option to move the infected files to a specific directory.  This directory needs to accessible by the 'clamav' user.

I would suspect that they were found in email attachments, would that be possible?  If thats the case then you just need to delete the emails with suspicious attachments.

---

### Post by kent41 on 2006-02-10
Clamav does not tell me the name of the files - it just says it found 4 
thanks for the reply i will look at the doc.

I don't use e-mails in linux.

---

### Post by Perfect Storm on 2006-02-10
You could try F-prot with XF-prot frontend: [http://ubuntuforums.org/showthread.php?t=88357](http://ubuntuforums.org/showthread.php?t=88357)

---

### Post by kent41 on 2006-02-10
what directory do i need to be in when in install F-prot ?

Thanks

---

### Post by Perfect Storm on 2006-02-10
well that depends where you downloaded F-prot to. If on desktop

```
cd Desktop
```

---

### Post by Mustard on 2006-02-10
Are you using some type of frontend gui for clam?

I've just got the command line version installed myself.

-edit-

Doh...seems the conversation has moved on without me noticing. :)

---

### Post by kent41 on 2006-02-10
Ok as you can tell I am new to linux and did not know if it made a difference where
you would install it.

Thanks

---

### Post by kent41 on 2006-02-10
[QUOTE=Mustard]Are you using some type of frontend gui for clam?

I've just got the command line version installed myself.

-edit-

Doh...seems the conversation has moved on without me noticing. :)[/QUOTE]


 No i just have the command line version. I get the summary message at the completion og the run

---

### Post by Mustard on 2006-02-10
[QUOTE=kent41]Ok as you can tell I am new to linux and did not know if it made a difference where
you would install it.

Thanks[/QUOTE]

The instructions are all in a link in an earlier post.  What part of the instructions are you having trouble with?

---

### Post by kent41 on 2006-02-10
Thanks  ******* MUSTARD********

I found in the CLAMAV documentation the  ( -i ) switch prints out only the 
infected files.  The files infected were Clamav files so I did not delete them.

Thanks again to  :) \\:D/  MUSTARD

---

### Post by Mustard on 2006-02-10
[QUOTE=kent41]Thanks  ******* MUSTARD********

I found in the CLAMAV documentation the  ( -i ) switch prints out only the 
infected files.  The files infected were Clamav files so I did not delete them.

Thanks again to  :) \\:D/  MUSTARD[/QUOTE]

Hehe..no problem.  So it was a false positive in the end. :)

It must have been scanning its own virus database.

---

### Post by Madpilot on 2006-02-10
[QUOTE=Mustard]Hehe..no problem.  So it was a false positive in the end. :)

It must have been scanning its own virus database.[/QUOTE]

That sounds like an interesting bug, and hardly useful behaviour from a virus scanner... might want to file that - [https://launchpad.net/distros/ubuntu/+bugs](https://launchpad.net/distros/ubuntu/+bugs) - you'll need to sign up there...

---

### Post by Micro Rotors on 2006-02-18
If I am not mistaken, the 4 files he is refuring to are test files.

---

### Post by nalmeth on 2006-02-18
So whats the deal with this? Are they windows viruses? Mistaken files? Ubuntu viruses?  What?

---

### Post by Lord Illidan on 2006-02-18
[quote=Micro Rotors]If I am not mistaken, the 4 files he is refuring to are test files.[/quote]

I think so too... Not a bug, it just confirms that it is working.

---

### Post by ToulCit on 2006-03-22
Hi all ,

I am new to Ubuntu and being used to windows i always had 2 virusscanners
Clamwin & Kasperksy and a hardware firewall and a software firewall.
Now that i use Linux i am less worried but i still feel the oppertunity to get infected still exist.
So i installed firestarter , wich i am not very happy with at all , it never asks me anything.
And i use F-prot , but i don't know how to scan all files.
I configured it to scan the /. directory , but then it hangs , and stops scanning.
Can anyone help me to scan all files?
I can also scan all maps manually , but i think that's too much of a fuss really.
And i also tried to install clam , using synaptic , but that didnt work well.
I installed clamtk manually , but it doesn't allow me to update since i am no root.
And from i read , you can't be a root in unbuntu , very safe :D.

---

