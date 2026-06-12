---
title: "how to restore the /home-map"
date: 2005-11-28
forum: Absolute Beginner Talk
---

### Post by Zunflappie on 2005-11-28
Stupid as I am, i edited the /home-map.
It was (before i edited it) */home/eddy*

I have changed that (stupid) to */home/eddy**/desktop***
If i want to start Ubuntu it gives a error that the /home-map doenst exicts. Oke... he wont continue.

I tried a fail-free-start AND a safe-mode-start > both didnt solve the problem.
I have did the recovery-mode (from boot-up, where to chose between Ubuntu, Ubuntu-recovery en Windows XP).

That didnt help.
I got a console over there (in recovery-mode).
But i dont know what to do.

Please help me by posting the solution.
The currect /home-map must be the same, minus /desktop.

Please... can anybody help me?
Otherwise I have to reinstall Linux... and thats a thing i DONT want to do...
If I have to reinstall Ubuntu... will I lose all data on that HDD?
Because then its NOT a option.

Please help me...

---

### Post by Zunflappie on 2005-11-28
Maybe some progress:

i started Ubuntu by its boot-screen (chose Windows or Linux).
There i could configure SOMETHING and got a commando-line :D:D:D

So, i can access the command-line. But i need to edit a file? Or the register? Or something else? I dont know.
I dont know either how. :( 

Can someone tell me?
Wich file do I have to edit? And how?


(i know: it sounds desperate... because I am :(:()

---

### Post by Zunflappie on 2005-11-28
YES.

I found a program ([http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm#Download)) where i could get my hands on my documents.
So now there again in my control.

With that program i can see and read ALL files on the Linux-hdd.
But NOT save/edit.

So, I have to repair Ubuntu using the command-line.
But I dont know how... can anybody tell me?
Otherwise I have to reinstall Ubuntu (costs time + settings etc...)

---

### Post by Kvark on 2005-11-28
How did you change your home dir from /home/eddy to /home/eddy/desktop in the first place? ...you must have done something to change that, just do the same thing again but choode /home/eddy this time.

My guess is that you edited /etc/passwd and changed your home dir in that file. If thats the case then type "nano /etc/passwd" to edit that file with nano and change it back.

---

### Post by Topsiho on 2005-11-28
[QUOTE=Zunflappie]Stupid as I am, i edited the /home-map.
It was (before i edited it) */eddy/home*[/QUOTE]

The "stupidity" must have happened earlier, as /eddy/home is already incorrect :)

It should have been /home/eddy and not the other way round.

The /home map contains the (configurations + personal) maps for all users of the system such as /home/eddy, /home/user1, /home/user2 etc.

How you reversed the order is not obvious to me, but it's clear that it was already wrong (if you are right :) with the information you give).

If this would have happened to me on a newly installed system I would reinstall again. Much the easiest way, and it gives you the opportunity to do some things in just another way, as you have gained some experience.

On the other hand: figuring out what has happened may teach you something which you would not learn if you follow my advice :).

Topsiho

---

### Post by Zunflappie on 2005-11-29
[QUOTE=Kvark]How did you change your home dir from /home/eddy to /home/eddy/desktop in the first place? ...you must have done something to change that, just do the same thing again but choode /home/eddy this time.

My guess is that you edited /etc/passwd and changed your home dir in that file. If thats the case then type "nano /etc/passwd" to edit that file with nano and change it back.[/QUOTE]

I did that by System/Options > Users

There you can set a home-map for a user.
There is 1 user: me.
There i changed the home-map.
So i dont have edited manual files. I used the configuration-screen.
It is possible thats in that file... i will try and found out.




[QUOTE=Topsiho]The "stupidity" must have happened earlier, as /eddy/home is already incorrect :)
[COLOR="Red"]thats a type-fault. Its /home/eddy insteed of /eddy/home.
So it is: /home/eddy/desktop[/COLOR]

It should have been /home/eddy and not the other way round.

The /home map contains the (configurations + personal) maps for all users of the system such as /home/eddy, /home/user1, /home/user2 etc.

How you reversed the order is not obvious to me, but it's clear that it was already wrong (if you are right :) with the information you give).

If this would have happened to me on a newly installed system I would reinstall again. Much the easiest way, and it gives you the opportunity to do some things in just another way, as you have gained some experience.

On the other hand: figuring out what has happened may teach you something which you would not learn if you follow my advice :).

Topsiho[/QUOTE]

Maybe, after trying previous advice, i will reinstall.
I have got my files... so thats no problem anymore.

---

### Post by Zunflappie on 2005-11-30
IT WORKED

In Windows i searched the file /etc/passwd

And it was there... the map-url.
In Ubuntu-restore-thing... used " nano /etc/passwd"

And it works :D

Thanks!
My thankness is great to you both! :cool:

---

### Post by Topsiho on 2005-12-01
Great, congratulations.

Topsiho

---

