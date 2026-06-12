---
title: "Has Anybody experienced this ???"
date: 2006-02-22
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-22
Hello All !!!

This is the first time I experience this !!!

After I installed a bunch of Software in My Ubuntu 5.10, I experienced the following:

... I was NOT able to make a POST inside this FORUM...

... YES, you are reading it correct !!!

After I typed in my username & password, I got into the "Proceed" button screen & then back to the "username" & "password" page!

Now: My username & password were typed correct (I assure you for this...) & I tried this MANY times (I also checked my keyboard that was set in the English typing status)...

... If my username & password were typed incorrectly, I assume, I would have NOT been moved to the "Proceed" buttoned Page...

Has anybody experienced this?

P.S. > How did I fix this, you will wonder...
         I formatted the Ubuntu again !!!
       ... only to realize that nothing got Fixed !!!
       ... and then I realized that I can Log-in **ONLY** from the Top Right Side of 
           the Ubuntu Forum Pages... What is wrong?
       ... So I guess, it has NOTHNG to do with Installing S-ware, it MUST be 
           something else...

---

### Post by Ghetto_Smurf on 2006-02-22
did you try to login in safe mode (no gdm)?

---

### Post by soc on 2006-02-22
so where did you log in before? the login in the upper right is the only way to log in .. or do i not see something?

---

### Post by Gowator on 2006-02-22
sounds to me like you just needed to clear your firefox (or other browser) cache not what sounbds like you reintalled ubuntu.  
However it can be hard when you are locked out for any reason (like intenret not working) and unable to get help ...  but usually things can be fixed without reinstalling.

---

### Post by dvarsam on 2006-02-22
Well, this is how I did in the past:

1. Log-out from YOUR account.

2. Close all your browser windows.

3. Launcht a browser window & in the Address type"http://www.ubuntuforum.org/"

4. Scroll down the page to find the "Absolute Beginner Talk" & click on it.

5. Select (or Click) on any Thread you would like to see (or enter).

6. Scroll down to the last response & click on the button named "New Reply" on your left (or "Quick 
   Reply" on the right).

7. A window comes up, asking for your "username" & "password"


This is how I did it in the past, with NO problem.


The only problem I had, was that:

If I did NOT type-in my "New Reply" post fast, I was thrown out & then I had to re-enter my account (and that means I had to re-type) my "username" & "password".

Now, sometimes, when I re-entered my "username" & "password", I would enter the Forum, but sometimes the "New Reply" (or "Quick Reply") Post, would NOT actually Post.

And, if I pressed on the Mozilla Firefox's Standard Toolbar button named "Go back one Page" (the "arrow"), I would go back, BUT my whole message would be erased !!! (I would have to re-type the whole reply...)

So, what I did was this:

I had ALWAYS 2 Mozilla Firefox windows open & if while typing my "New Reply" or "Quick Reply" (in one of them), I was taking TOO long & was thrown out of the Forum, with the 2nd Mozilla Firefox window, I I would log-in & then copy&paste the (now finished) "New Reply" from the first Mozilla Window to the Second & with no delay (and no chance to be thrown out - since I did it fast), the "New Reply" post was Posted fine !!!

Now, for some reason, I can NOT Log-in with the above Method.

And I am FORCED to Log-in from the Upper-Right corner of the Forum's Pages.

Try it out & respond...

---

### Post by dvarsam on 2006-02-22
Sorry guys, I had to post the above, the fastest possible, because now I can NOT Log-in - NOT even from the TOP Right side of this Forum's window.

Of course, you will ask:
If YOU can NOT Log-in, then How are you replying to US with YOUR Posts?

I tried this:

I first SELECT the Forum I want to Enter (e.g. The Beginners Forum) & then I try to Log-in to MY account.

In the PAST, I could type my "username" & "password" in ANY Forum's window to enter to my account !!!

Now I FIRST have to move to the "Begginers Forum" & THEN I can type my "username" & "password" to Log-in...

As if the Administration has CHANGED (or Separated) the access priviledges to be able to access EACH SUB-Forum.

So I need ONE account for EVERY sub-forum, I do NOT get this...

---

### Post by LordBug on 2006-02-22
This really sounds like a cookie issue.  Launch 1 Firefox instance, and clear out your cache and cookies.  I've had similar oddball login issues with other sites, and a cookie purge clears it up.

---

### Post by Gowator on 2006-02-22
Firstly did you check the remember me ?
it can be helpful but sometimes you need to clear out the cache as I said above. 

You say you are using firefox so firdst go and clear all cookies etc, for this site 
Edit/Preferences then privacy and eithwer edit and find the 3 cookies for forums.gentoo.org OR clear all ... (will loose all other stuff but not a bad thing to do from time to time)
While you are there you can clear cache too.  

Now when you log in make sure you click remember me...

---

### Post by ronmarley1 on 2006-02-22
Hey Everybody,
I just started a thread on this also (sorry I did not search first).  This just started today (worked fine last night).  Everything works fine on Firefox on Windows XP, but not on Ubuntu.  It's a weird one.  Here's the link to the thread:
[http://ubuntuforums.org/showthread.php?t=134756&highlight=cookies](http://ubuntuforums.org/showthread.php?t=134756&highlight=cookies)

---

### Post by ronmarley1 on 2006-02-22
dvarsam,
did you install firefox using automatix?  I did to save some time after a rebuild.  that's the only thing i can think of that i did differently from my last build.

---

### Post by ronmarley1 on 2006-02-22
**[COLOR="Red"]SOLUTION![/COLOR]**  On a hunch, I did this, and it fixed it!
open a shell and delete the file "default.keyring" in $HOME/.gnome2/keyrings/
you'll loose all the passwords but can set a new default keyring password next time nautilus asks you.

---

### Post by dvarsam on 2006-02-22
I was talking about a CLEAN Ubuntu Install !

Remember - I FORMATTED my Hard Drive & Re-installed...

... And still I had problems posting...

I had installed NOTHING else on my system & Could NOT Log-in !!!

So, NO, I did not use Automatix (I did NOT use anything at all).

I even thought that somebody could have hijacked my account...

... maybe somebody knew (or hacked) my "username" & "password" & logged-in,

so I could NOT log-in at the same time...


... Now, whenever I try to Log-in, I just click on the "Remember Me" button (as suggested).

At the same time I have SET the Ubuntu Forum's Cookies as "Always Permitted".

Now I do NOT have a problem but who knows what may happen in the Future...

_My only worry (concern) is this_:

If for some reason in the FUTURE I can NOT post questions about my Ubuntu's problems, in THIS Forum, then I would be "Forced" to return to the Windows Platform (which I dislike - if not HATE).

---

### Post by ronmarley1 on 2006-02-23
Man, that really sucks.  I felt the same way about being able to post, and ditching Linux, but I got lucky.  Did you try deleting the keyring file?  Good luck...  Don't loose the faith!

---

