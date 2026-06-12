---
title: "Unmounting a Floppy Disk - I think I Found a Bug"
date: 2006-04-01
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-04-01
Hello All!!!

I performed this:

1. I launched a Terminal & logged-in as Root.
2. I mounted a floppy disk
3. I entered & did some stuff
4. While I was inside the floppy folder (e.g. in "/media/floppy0"), I decided to "umount" the floppy.

_Outcome_:
> umount: /media/floppy0: device is busy

I tried to umount repeatedly, ONLY to get the SAME above message...

I later realized, that because I was unmounting the Floppy from inside, it could NOT "umount".

I had to perform a "cd /" (to get outside the floppy) & then perform the "umount"

_Solution_:
Ubuntu programmers should FIX this.
Example:
IF I am lying INSIDE the Floppy & want to "umount", I should be ABLE to perform that operation...

AND probably, my Terminal prompt should go BACK as many directories as it needs to get out from the Floppy contents OR at least return me to the Root Directory!

The Terminal telling me that "device is busy", is NOT good...

In such a case, ALL I really want is to "umount" my Floppy...

OK, mistakenly I was doing this from withig the Floppy!!!

So what?

That does NOT mean, that I did not know what I was doing...

It should be programmed to _perform_ that operation...

What do you think?

Thanks.

P.S.> Can somebody post this in the Ubuntu BUG Reports? Thanks.
        If you do, please mention it in THIS post, so that the BUG Reports do 
        NOT get dozens of posts for the SAME problem. Thanks.

---

### Post by Pragmatist on 2006-04-01
Useability is very important; I agree with you on that.

However, your complaint is misplaced in this case.  It is totally intuitive that you should NOT be able to unmount a device while still inside the device file.  What your asking is equivalent to saying, "I should be able to make a new filesystem on the partition I'm currently working on without first unmounting it".  

When you mount a device to a file, to Linux the device and the file are one and the same thing.  When you unmount the file, from Linux's perspective, you are disconnecting the device from that file.  So that means your telling Linux that you are in the device and then disconnect the device!  How do you get out?

Anyway, it is more complicated than that, I am sure.  However, to 'fix' your complaint would require completely redesigning the operating system, including a MAJOR change to its entire philosophy of treating everything as a file.

---

### Post by dvarsam on 2006-04-01
> **Pragmatist]Useability is very important said:**
> 

I disagree Totally!!!

IF (by a slight mistake) I ask a Drive/Partition to "umount", it should NOT matter whether I am INSIDE or OUTSIDE when asking...
It SHOULD do what I asked, AS LONG AS there are no current processes working on that Drive/Partition!
AND being INSIDE that Drive/Partition, can NOT be considered as a process!

Example:
I am copying a Huge file from Hard Drive 1 to Hard Drive 2.
During the process, I decide to "unmount" Hard Drive 2.
THIS should NOT be possible since I am running a process!

If NO processes relating to my Hard Drive 2  were in progress, EVEN if I were inside the Hard Drive 2, when asking, it should go on & do it!!!

Your Point is NOT correct, man...

I will give you another Example: Using Shortcuts!!!

1. Create a Shortcut pointing to another Hard Drive's Directory.
2. Unmount the Hard Drive.
3. Double-click on your Shortcut to access that Hard Drive's Directory.

Why does it Re-direct to my Home or Desktop folder, man?

Maybe it should say: "Device is busy" or "Device does Not Exist"!

The SAME thing could happen with the "Unmount" command!!!

Re-direct my Terminal to the "Root" Directory OR to the First Directory lying outside that Drive/Partition's Access Folder!

> 
What your asking is equivalent to saying, "I should be able to make a new filesystem on the partition I'm currently working on without first unmounting it".

You are taking/pushing it too far......

AND you know exactly what I am saying & that it is VERY logical.

Sometimes we need to "cut" the "device is busy" crap & simply do what we asked....
AND this was something VERY easy - I did NOT ask Ubuntu to launch a Rocket to the Moon man...

[QUOTE]
When you mount a device to a file, to Linux the device and the file are one and the same thing.
When you unmount the file, from Linux's perspective, you are disconnecting the device from that file.
So that means your telling Linux that you are in the device and then disconnect the device!  How do you get out?


With simple programming man!!!
It is the Programmers job to do that!
AND it makes sense!!!
What does the "device is busy" really mean man?
It could as easily say "please move out from the drive & then try to umount".
Wouldn't that make more sense?

> 
However, to 'fix' your complaint would require completely redesigning the operating system, including a MAJOR change to its entire philosophy of treating everything as a file.

---

### Post by dvarsam on 2006-04-01
Sorry, but by mistake, I pressed enter & it got posted!

> 
However, to 'fix' your complaint would require completely redesigning the operating system, including a MAJOR change to its entire philosophy of treating everything as a file.

To answer your last comment:

This is "b*llsh*t"!
It would only require just a few lines of programming commands, saying, this:


IF the disk/partition is asked to umount from inside & no other running processes using that partition are in progress, unmount the partition.
At the same time, move the Terminal prompt to the Root Directory!

That simple!

---

### Post by Pragmatist on 2006-04-01
1. Even if your right, it wouldn't be a bug. It would be a feature that is missing. A bug means that there is some interference with the way the program was intended to run. You could change directories and everything works. There are directions that explain that. So...it is not a bug.

2. Your not right (sorry).  To demonstrate:

(a) Why can't you remove a directory while your still inside it?  That is exactly what your doing when you unmount a device.

(b) To quote the mount man page:
>    mount -t type device dir
       This tells the kernel to attach the file system found on device (which is  of  type type)  at  the directory dir.  **The previous contents (if any) and owner and mode of dir become _invisible_**,** and _as long as this file system remains mounted, the pathname dir refers to the __root of the __file system on device._**
 
What _you_ are suggesting is that after you unmount /media/floppy you should remain in /media/floppy.  But they are **two different files**.  To prove this to yourself, do this experiment:

1.) cd into /media/floppy
2.) copy some files into /media/floppy when no drive is mounted to it.
3.) type **ls** to make sure your files are there?
4.) mount your floppy drive to /media/floppy while your still in /media/floppy
5.)  type: **ls**
6.)  How about now? Do you see the original files?
7.) type: **cd ..**  to change out of the directory you are unmounting
8.) unmount /media/floppy
9.) type: **ls floppy**
9.) Are your original files there now?

The reason you can mount while you are inside /media/floppy is because the filesystem of the drive isn't mounted until you access it (by typing **ls** for example)

> 
 This is "b*llsh*t"!
 It would only require just a few lines of programming commands, saying, this: 
Even though what your suggesting is absurd...if you really think it can be done...Prove it, don't state it! Which lines would you add and where would you add them?

Enough said; Case closed.

---

### Post by tadashi on 2006-04-01
The OS does this for a reason.  You may have other programs working in a directory your are deleting or unmounting.  By forcing the unmount you can cause unstability.  At best I would suggest you have to type a flag to force it if you want so you cannot just do it by accident.

---

### Post by dvarsam on 2006-04-02
> **Pragmatist]1. Even if your right, it wouldn't be a bug. It would be a feature that is missing. A bug means that there is some interference with the way the program was intended to run. You could change directories and everything works. There are directions that explain that. So...it is not a bug.
[/QUOTE]

OK, YES!
I Agree with you on that!!!

> 
2. Your not right (sorry).  To demonstrate:

(a) Why can't you remove a directory while your still inside it?  That is exactly what your doing when you unmount a device.


Yes, this is what I am doing when unmounting a device...
And IF it were NOT used by some other running process, it should be able to do it!

> 
(b) To quote the mount man page:
 
What _you_ are suggesting is that after you unmount /media/floppy you should remain in /media/floppy.  But they are **two different files**.


OK, if that is your problem, do it in the opposite way, like this:

IF the disk/partition is asked to umount from inside & no other running processes using that partition are in progress:

a. Move the Terminal prompt to the Root Directory,
b. AND then, unmount the partition.

> 
To prove this to yourself, do this experiment:

1.) cd into /media/floppy
2.) copy some files into /media/floppy when NO drive is mounted to it.
3.) type **ls** to make sure your files are there?
4.) mount your floppy drive to /media/floppy while your still in /media/floppy
5.)  type: **ls**
6.)  How about now? Do you see the original files?
7.) type: **cd ..**  to change out of the directory you are unmounting
8.) unmount /media/floppy
9.) type: **ls floppy**
9.) Are your original files there now?

The reason you can mount while you are inside /media/floppy is because the filesystem of the drive isn't mounted until you access it (by typing **ls** for example)


Answers to Steps you Suggested:

3. Yes they are there!

5. Yes they are there - but I am basically NOT looking at the floppy contents.
    THIS IS A POOR "LINUX OS" DESIGN!!! The REAL Floppy's contens are in fact EMPTY!!!

6. Yes they are there! - but this is NOT the floppy contents I am looking!

7. I did that...no ploblem!

7,5. I added the following step here:
      Move back inside the "floppy0" directory (e.g. type: "cd /media/floppy0")
      Perform an "ls" command. Do you see the original files?

     _ Answer_:
     NO, I do not see them! Because ONLY NOW I am _actually_ seeing the contents of the Floppy!
     _Conclusion_:
     THIS IS A POOR "LINUX OS" DESIGN!!!

      _How to FIX this_:
      a. Nobody should be able to copy files in an unmounted Floppy Drive!!!
          The path '/media/floppy0" SHOULD be Dedicated ONLY to a REAL floppy! It should NOT function as a REGULAR Directory too!
It should be designed to print:
"Sorry but this folder is dedicated to the Floppy! Mount it first & then try to copy stuff inside."
Now, if you want to "mount" the Floppy Drive to a different Directory, that is a different case. Do as you wish! But AT LEAST the directory "/media/floppy0" should be DEDICATED ONLY to the Floppy!
Don't design it like "Dr. Jekyl & Mr. Hyde"!

> 
Even though what your suggesting is absurd...if you really think it can be done...Prove it, don't state it! Which lines would you add and where would you add them?


What you call "absurd", I call it simply "logical".
Just because it was designed "wrong" does NOT mean that the whole world has to be "functioning" wrong...

Some files, at "least" have to be Dedicated for what they are designed for...
And it seems to me that "/media/floppy0" was designed so that WE mount floppies...

Real life example:

You get married to a girl...
Do you want your wife to start "cheating" on you... NO!!!
You do NOT want her to act as "Dr. Jekyl & Mr. Hyde"!
You want a "Loyal" wife.
You want her "designed" to be "Loyal"!

That is what I want My "Ubuntu's" OS to do, "AT LEAST" on the "/media/floppy0" folder - TO DEDICATE IT ONLY FOR _ONE_ PURPOSE!!! 
Otherwise, delete the whole "/media" directory...
I could do mounting wherever I want...
Why should it EXIST in the first place?

So, if I go on your side/point, I could mount a floppy anywhere...(and I know I can!)... and then the "/media/floppy0" is OBSOLETE!!!
They should DELETE ti, anyway, right???? (it is working like a normal directory, ain't it? Let's make the Ubuntu OS look "alien" & go ahead and delete ALL obsolete or empty directories...)

...But when I think again... it was designed for mounting Floppies...???
OR: was it not?
IF it "were" DESIGNED for that purpose, they should probably make it work right!!!

And leave the REST as is!!! (meaning: to be able to mount floppies elsewhere too!!! - that is a choice of every user - on an individual basis).

[/QUOTE]Enough said said:**
> 

No problem, but it is STILL Poorly Designed!

P.S.> Now, if you were asking me:
        [QUOTE]Is this the BIGGEST" problem you have with your Ubuntu?"

NO, it is NOT! I would prefer if the Programmers fixed FIRST the problems with installing ".tar.gz" packages... Cause that is a chaos... man...
AND to add something here, if we (almost) "always" have to install those "build-essential", why don't they MAKE it be installed BY DEFAULT?

Thanks man!

---

### Post by steve.horsley on 2006-04-02
[QUOTE=dvarsam]OK, YES!
OK, if that is your problem, do it in the opposite way, like this:

IF the disk/partition is asked to umount from inside & no other running processes using that partition are in progress:

a. Move the Terminal prompt to the Root Directory,
b. AND then, unmount the partition.
[/QUOTE]
There are many difficulties to be solved before you can do this. 
Just on efor instance might be: what happens if the process is in a chroot jail and not allowed out of that filesystem? 

I believe that a rule that says you can't unmount a filesystem that is in use is clear and safe. Adding exceptions to the rule is adding complications and risks unnecessarily.

> 
     _ Answer_:
     NO, I do not see them! Because ONLY NOW I am _actually_ seeing the contents of the Floppy!
     _Conclusion_:
     THIS IS A POOR "LINUX OS" DESIGN!!!

      _How to FIX this_:
      a. Nobody should be able to copy files in an unmounted Floppy Drive!!!
          The path '/media/floppy0" SHOULD be Dedicated ONLY to a REAL floppy! It should NOT function as a REGULAR Directory too!
It should be designed to print:
"Sorry but this folder is dedicated to the Floppy! Mount it first & then try to copy stuff inside."
Now, if you want to "mount" the Floppy Drive to a different Directory, that is a different case. Do as you wish! But AT LEAST the directory "/media/floppy0" should be DEDICATED ONLY to the Floppy!
Don't design it like "Dr. Jekyl & Mr. Hyde"!


Any directory in the filesystem is potentially a mount point. Including "/". And it is not possible to "reserve" directories such that they cannot be accessed until a foreign filesystem has meen mounted there. This is the way all unixes have worked. You can't blame Linux, it just copied what Unix does. If you want to blame anyone, blame the guys at Bell Labs who invented Unix. But I'm sure they must have a good reason for having done it that way. 

I would have thought making a completely new directory appear and disappear would have been more understandable, but that's not the way it is. I suppose that if the kernel works by creating an in-memory "/" and then mounting the root hard-disk partition at that point, then changing mount so that it can only add new directories would have meant that no files or folders could ever be actually saved in the root directory. It may have been a fairly simple chioce at the time. Whatever the reason, it is done now, and will remain so, in the same way that driving on the left or right will remain, now the choice has been made.

---

### Post by dvarsam on 2006-04-02
[QUOTE=tadashi]The OS does this for a reason.  You may have other programs working in a directory your are deleting or unmounting.[/QUOTE]

If you read my full post, I covered that possibility...

_I said_:
"unmount ONLY if there are NO other processes using that drive/partition."

[/QUOTE]By forcing the unmount you can cause unstability.[/QUOTE]

IF I was  "asking" to unmount from inside, and the OS first moved out of the directory & then "umount", there should be no problem & NO "forcing" anybody...

> At best I would suggest you have to type a flag to force it if you want so you cannot just do it by accident.

Call it a "flag" or .... a "rooster" if you wish...
And I was NOT unmounting by accident...

_The "accident" had to do_:
with me asking the OS to "umount" while I was inside that disk/partition...
I (by mistake) asked Ubuntu to "unmount" while beind inside "/media/floppy0".
It did NOT have to do with _mistyping_ a command!

AND the OS should be designed to understand what I did, correct my mistake & "unmount".
It is the SAME as "spell checkers"...man.
They know I mis-spelled a word!
And in some times they correct it automatically & in other times they require my "intervention" to correct the words or not.

_In_ _this_ "unmount" _case_, it should do what is "obvious" & go ahead & _automatically_ "unmount".
NO warning "device is busy" should be printed & no other "intervention" should be asked/required from my side...

Thanks.

---

### Post by dvarsam on 2006-04-02
[QUOTE=steve.horsley]There are many difficulties to be solved before you can do this. 
Just on efor instance might be: what happens if the process is in a chroot jail and not allowed out of that filesystem? 
[/QUOTE]

I did not understand the "chroot jail" process...
Sorry man, I am not so programming oriented...
But if this belongs to a "diff" process, other than the "umount", then it is logical to get the "device is busy" output.
Then wait untill the process ends & do what I asked & me retype what I want again. 

> 
I believe that a rule that says you can't unmount a filesystem that is in use is clear and safe. Adding exceptions to the rule is adding complications and risks unnecessarily.

If you are a programmer, then it is _your_ JOB to make it work safe.
Just because they are lazy, or do NOT want to type extra stuff, does NOT mean that things should be working NOT correctly...

> 
Any directory in the filesystem is potentially a mount point. Including "/". And it is not possible to "reserve" directories such that they cannot be accessed until a foreign filesystem has meen mounted there. This is the way all unixes have worked. You can't blame Linux, it just copied what Unix does. If you want to blame anyone, blame the guys at Bell Labs who invented Unix. But I'm sure they must have a good reason for having done it that way. 
[QUOTE]

One hundred years ago, our ancestors were riding horses...
Now we are using cars.
You can NOT blame the horses for that.
I may NOT be blaming "unix"...
...but that does NOT mean that I should continue to ride that "horse" today...
So, don't ask me to use that old "unix" technology...
Things advance, so does technology...
I can NOT have the SAME expectations from "Linux", if I want to consider it a more advanced system than "unix".

[QUOTE]
I would have thought making a completely new directory appear and disappear would have been more understandable, but that's not the way it is.


If you do the appear/disappear case, you might end up with users saying that it did NOT appear in their systems...
Better to keep it appeared at ALL times...

> 
I suppose that if the kernel works by creating an in-memory "/" and then mounting the root hard-disk partition at that point,...

... then changing mount so that it can only add new directories would have meant that no files or folders could ever be actually saved in the root directory.

I did not get that second part...

> 
It may have been a fairly simple chioce at the time. Whatever the reason, it is done now, and will remain so, in the same way that driving on the left or right will remain, now the choice has been made.

There is always a choice to correct things done wrongly...

Thanks.

---

### Post by dvarsam on 2006-04-02
Edit:

Please change:

...Then wait untill the process ends & do what I asked & me retype what I want again.

With:
..Then wait untill the process ends & do what I asked _OR_ me retype what I want again.

---

### Post by Pragmatist on 2006-04-02
Do you hear yourself?
 
 1.) You say your not "so programming oriented..."
 
 2.) You say you know what is right or wrong with an incredibly complex program that millions of people have used over the years.
 
 3.) Have you ever wondered why this hasn't come up before?  Do you think you are such a genius of computer OS design that you thought of this, but millions of others (everybody from computer programmers to people like you) have not thought of it?  This isn't Microsoft.  Linux makes changes through a huge network of users worldwide.  Why wouldn't _one_ of the other millions of users think of what your saying--especially if it is so obvious a mistake???
 
 *4.) Your problem, btw, is not distribution-specific, so Ubuntu has nothing to do with it. You'd have your same problem with any Linux distribution (or Unix distribution, or MAC OSX or Windows, etc...)*
 
 5.) Your general, simplistic, idea is that "if no process is using it, I should be able to do whatever I want with it".  Of course, according to you, one should be able to delete directories while still located inside of them--even though **NO OPERATING SYSTEM does this**, or every will!!!  If you say that we should not be able to do this, then we shouldn't be able to do what you want because unmounting while still in the mount point is exactly the same as removing a directory while still located there.  You say that the OS is responsible to move you around if you made the mistake of being in the wrong place!!  Where do you draw the line between a dumb mistake that you make and the responsibility of the OS?  What if you accidentally type: **rm -r / home/user/directory **Now you just removed the entire contents of root!! because you accidentally put a space after the first /  Now there are protections you can use (like creating an alias to rm making it rm -i to be interactive. Then you have to confirm each file deletion--of course even here, you could have typed **rm -rf / home/user/directory** and it would be no good.), but they aren't created by the OS. They are options for the user.  Some users choose to use them and some don't. Some distributions have those features on by default and some do not.
 
 6.) It seems to me that the inception of your idea was a frustrating experience born from ignorance.  You got mad that things didn't work the way you mistakenly believed it should.  Now, rather than admit you made a mistake, you are complaining that the mistake is with the computer, not you.  Even if you did not say that you were unfamiliar with programming, I would already know that.  The reason is that programmers learn very early that ego is a big hinderance to progress.  If you want to get better at using Linux, or any other aspect of computers, you need to be totally comfortable with making mistakes and totally comfortable with *taking responsibility for those mistakes.*

---

### Post by dvarsam on 2006-04-02
[QUOTE=Pragmatist]Do you hear yourself?
 
 1.) You say your not "so programming oriented..."
[/QUOTE]

I have only had 1 semester of programming man...

> 
 2.) You say you know what is right or wrong with an incredibly complex program that millions of people have used over the years.
 

All I said, was that it did NOT work "correctly" & could have been better man...

> 
 3.) Have you ever wondered why this hasn't come up before?  Do you think you are such a genius of computer OS design that you thought of this, but millions of others (everybody from computer programmers to people like you) have not thought of it?  This isn't Microsoft.  Linux makes changes through a huge network of users worldwide.  Why wouldn't _one_ of the other millions of users think of what your saying--especially if it is so obvious a mistake???


Maybe NOBODY bothers as much as I do man....
But Microsoft at least performs better on this man...

Please do not take this in the wrong way:

I like my Ubuntu very much!
Wantings things to work better can NOT harm anybody...
I like to post stuff, when I feel they are NOT working man...

Besides, if the Linux programmers close their ears to the outside world, the OS they make, will have the destiny/prospects of Microsoft's Windows...
It will finally get "dumped"...

ALL I want, is a better (possible) working OS...

Besides, we all want this...

NOW, I do NOT know why you are trying to make me look dumb or st*pid man...

Maybe you belong to the "Ubuntu Staff" or something & you prefer to make me look "st*pid" than to admit that it could work better...
... and that this is very feasible to do be done...

> 
 *4.) Your problem, btw, is not distribution-specific, so Ubuntu has nothing to do with it. You'd have your same problem with any Linux distribution (or Unix distribution, or MAC OSX or Windows, etc...)*
 

No problem...
Then, maybe ALL the Linux community should sit down & do something about it...
I am NOT blaming anybody on this...
I am just pointing out how could things work better...

> 
 5.) Your general, simplistic, idea is that "if no process is using it, I should be able to do whatever I want with it".  Of course, according to you, one should be able to delete directories while still located inside of them--even though **NO OPERATING SYSTEM does this**, or ever will!!!  If you say that we should not be able to do this, then we shouldn't be able to do what you want because unmounting while still in the mount point is exactly the same as removing a directory while still located there.  You say that the OS is responsible to move you around if you made the mistake of being in the wrong place!!  Where do you draw the line between a dumb mistake that you make and the responsibility of the OS?  What if you accidentally type: **rm -r / home/user/directory **Now you just removed the entire contents of root!! because you accidentally put a space after the first /  Now there are protections you can use (like creating an alias to rm making it rm -i to be interactive. Then you have to confirm each file deletion--of course even here, you could have typed **rm -rf / home/user/directory** and it would be no good.), but they aren't created by the OS. They are options for the user.  Some users choose to use them and some don't. Some distributions have those features on by default and some do not.


Deleting a Directory & unmounting is a different story...
However, that sounds interesting...
When deleting, you should always be asked...
Unless you are programming in bash...

So, YES, maybe deleting should be ALSO done like this...
It is nice you mentioned it...
And just because Nobody is using it, does NOT mean it is wrong if it were implemented...

Cellular phones did not exist 20 years ago...
That does NOT mean that implementing such technology is wrong...
And because it was not commonly used in the past, does not mean that is is a RULE for the future...NOT to be used...

Regarding the deletion of stuff, you can NOT blame the OS for that...
It is common sense that we ALSO hold responsibility for our "typing" mistakes...
But doing what I did can not be considered (at least by me) a mistake...
What I did, did NOT harm anybody...
...and Ubuntu (or other Linux OS's) could be designed better on this...

> 
 6.) It seems to me that the inception of your idea was a frustrating experience born from ignorance.  You got mad that things didn't work the way you mistakenly believed it should.  Now, rather than admit you made a mistake, you are complaining that the mistake is with the computer, not you.  Even if you did not say that you were unfamiliar with programming, I would already know that.  The reason is that programmers learn very early that ego is a big hinderance to progress.  If you want to get better at using Linux, or any other aspect of computers, you need to be totally comfortable with making mistakes and totally comfortable with *taking responsibility for those mistakes.*

No matter how much knowledge I acquire throughout my life, I will never be able to claim "knowledgeable" in EVERY SUBJECT...
And I can NEVER agree that it was the correct way, my Ubuntu OS responded on this...
I support the community 100% & all effort involved here, but I have the right to judge for myself what is better or worse...
So, NO I do NOT accept that it is my mistake...
(I understand I should be outside the floppy when "unmount", but I am human and mighr repeat this in the future... - Ubuntu should be able to help me out in such cases... and if it can understand what I want to do, push it through... not dump me, warn me, etc...)
And I am not an "egoist" as you imply...
I like to be skeptical at stuff & what I experienced with using the "unmount", I think that it is not designed well...

If I make mistakes, I take responsibility, you be sure about it...
But from mistakes, you learn...and become better...
Even OS design, gets better only after realizing the mistakes...
When the SAME thing happens to you, maybe you will think about this twice man...
I brought this up, because I thought it could be designed better...
So, maybe you shoud NOT be so FANATIC supporting the Ubuntu man...

I love my Ubuntu too!!!

But at least, when it comes to pinpointing flaws or stuff that should be improved, it tend to bring them up...

...while you try to "soften" them out or "burry" them...

Thanks for your time.

P.S.> I guess that we can agree that we dissagree! LOL
        No harm feelings man - just difference in opinions...

---

### Post by Pragmatist on 2006-04-02
>  Even OS design, gets better only after realizing the mistakes...
  When the SAME thing happens to you, maybe you will think about this twice man...
  I brought this up, because I thought it could be designed better...
  So, maybe you shoud NOT be so FANATIC supporting the Ubuntu man...
 
 I am not a fanatic for Ubuntu and I'm not particularly committed to it or even Linux. I've used at least a dozen different distributions of Linux, and Win 3.1, 95, 98, 2000, and XP and MAC OS X
 
 I use whichever operating system serves my purpose and I use different OS for different tasks.  So I'm definitely not commited to an OS, much less a distribution.
 
 What I don't do, however, is decide what is CORRECT or WRONG with an OS unless I fully UNDERSTAND how the OS works.  Since you like analogies, I'll give you two:  Painting--Picasso, Da Vinci, Van Gogh ALL learned how to paint according to classical theory BEFORE innovating.  They understood what came before them before presuming they could improve on it.  Music--Famous quote of Mozart when asked by a politician to change his music because ('it had too many notes') He said, "Which notes should I leave out?".  It is OK TO CRITICIZE but it is meaningless if you can't offer A BETTER ALTERNATIVE.  Your saying what "should" be.  Your not saying "how" it can be done.
 
 It would be different if you came here and ASKED why it couldn't be the way you'd prefer.  Then, when those more knowledgeable than you explained it, you could decide if the way you prefer is better (or "correct").  But instead you came here and DECLARE that the OS contains something that is INCORRECT.  That requires understanding to decide if it is wrong or incorrect.  To say "I don't like it".  That is different.  To say "It is incorrect".  That you must PROVE.  So I ask again:
 
 _**Exactly which code would you change?  How would you change it?**_
 _**BE SPECIFIC**_
 
 Among other things, what your missing is that to make the change you want you might have to change MANY other things to make it work.  You might even have to change the entire philosophy of how Unix/Linux is based on.  You say this is ridiculous, but do you UNDERSTAND the Linux philosophy when it comes to treating everything as a file?
 
 Regarding deleting/removing files.  You missed my point.  You can put all the protections you want in place.  If you want the flexibility and freedom of options, you take more reponsibility and risk and complexity:
 
 [B]More flexibility/options = More complexity/responsibility/risk
[/B]
 One of the reasons that Microsoft "does it right" (assuming it does) is because microsoft limits your options.  For example, you can't see the source code of Windows.  If you could see it, you might make a dumb mistake by changing it incorrectly (although that isn't the reason they don't give it to us).  In Linux you could change the code, you use a shell (which protect you from the kernel/OS and therefore limits you somewhat--but that is for your and the OSes protection) and the shell provides some protection and also gives you the ability to completely screw up your system.  **It is always a difficult balance to decide what choices to make for people and what choices to let them make themselves. ** What your suggesting doesn't prevent problems.  It just prevents some annoyance for you.  If you just change out of the directory you'll be fine.  If you forget to change out of the directory, you'll get an error message.  Nothing bad happens, except you wasted a little time. Then you'll change out of the directory.  There are lots of ways to waste time if you don't follow instructions or try and do things that are impossible.  Every time you do, are we to change the whole OS around so that you don't annoy yourself by typing something that doesn't work and then having to type a little more??  If you add up all the typing you've done so far in this thread, you could have used that to correct 100 of the same mistakes.  If you forget that much, though, AND it bothers you to forget, you shouldn't be using the command-line.
 
 I'm not trying to make YOU look stupid.  How can I know if you are stupid?  I don't even know you. The IDEA your suggesting is stupid (I prefer ignorant.  If you understood more, then you wouldn't suggest it.)  You can be a very smart guy with a dumb idea.  Seperate the person from their behavior.
 
 Bottom line: It is perfectly alright to make SUGGESTIONS and be willing to agree if you are wrong (not to say, I AM RIGHT NO MATTER WHAT ELSE I LEARN!!!!).  _***There is a different between making an improvement for everybody and making an improvement for you.***_

---

### Post by NeghVar on 2006-04-02
> All I said, was that it did NOT work "correctly" & could have been better man...

Define correctly, in your deffinition correctly appears to mean the way YOU want. To everyone else it means that it does what it was supposed to do. It was programmed that way for a reason, and I don't think it is unreasonable to do it this way either. 

> Maybe NOBODY bothers as much as I do man....
But Microsoft at least performs better on this man...

This gets brought up everyother day, let me explain it to you, we ARE NOT Microsoft. Don't expect the exact same thing to happen, keep in mind with MS when you do those critical solitaire updates that are required every 4 hours that it also requires the restart of your computer before it sprouts wings,turns blue (or if it already is blue then red) and flys away.

> Wantings things to work better can NOT harm anybody...
I like to post stuff, when I feel they are NOT working man...

Once again what is 'better'  and how do you define not working, it really does seem like you made a mistake and because it made you mad you are taking it out on a design concpet that has been around for how many decades?

> Maybe you belong to the "Ubuntu Staff" or something & you prefer to make me look "st*pid" than to admit that it could work better...
... and that this is very feasible to do be done...

If this is so easy to complete why not just write a script that forces you out and then unmounts, then submit that script to the customization thingy. This seems like the easiest way to solve your problem.

> Then, maybe ALL the Linux community should sit down & do something about it...

Oh I love this, one man thinks the rest of the community i stupid, forces them to change to meet his specific needs...

As someones signature says, "Talk is cheap, Show me the Code." Cant remember which member has that.

---

