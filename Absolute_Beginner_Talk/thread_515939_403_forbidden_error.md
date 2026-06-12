---
title: "403 forbidden error"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Mr. Svinlesha on 2007-08-02
Hej.

I just reinstalled Ubuntu (edgy eft) from CD (double boot), downloaded 175 updates, and then upgraded to Feisty Fawn.  Everything seemed to work without a hitch, except for one minor problem: I don't seem to be able to download and install updates or packages: I keep getting a 403: forbidden error message when I try.

Anybody out there have an explanation, or solution?

---

### Post by Mr. Svinlesha on 2007-08-02
bump

---

### Post by Mr. Svinlesha on 2007-08-02
Is there no one out there who can help me with this problem?  It seems similar to one thry had in april, caused by a buggy kernal -- but the solution suggested for the problem won't work for me, since I don't have the relevant file in my boot folder.

---

### Post by Rocket2DMn on 2007-08-02
Can you post the contents of your /etc/apt/sources.list file?  It sounds like your list of repos may be outdated.

---

### Post by Mr. Svinlesha on 2007-08-02
Rocket:

After my last post I solved the problem by switching to a different download server.  It was that simple.

Thanks anyway for your reply!

:)

---

### Post by Rocket2DMn on 2007-08-02
I figured as much (hence the out of date repos), glad you got it figured out.

---

### Post by Alterax on 2007-08-02
403 errors I've only seen in reference to websites not allowing access.  What I do know is that apt-get uses http to pull in packages.  Put the two together, and it looks like you are not able to get packages because you are forbidden access to one or more of the repos that you are trying to pull software in from.

Here's an idea:  

Check your software repositories list:  System > Administration > software sources.  Enter your password (since it requires administrative privileges to run), and go to the third party software tab. Uncheck all of these boxes, then click Close.  You will get a pop-up window stating that the software list is out of date.  Click the refresh button and then try to install a program from the standard repository.

If this works, then the problem is somewhere in your third-party software sources, more than likely one that requires a key.  Remove all of them (yes, all of the third-party ones, especially the ones starting with [https://)](https://)) and then add them back in, one at a time, just like you did originally.  After that, you should be up and running.

Let me know if this helps!

--Alterax

---

### Post by Alterax on 2007-08-02
*LOL* Or you could try a different download server, I suppose...

Great to see it's working for you again.

--A

---

### Post by Mr. Svinlesha on 2007-08-02
alterax:

:)

Thanks all the same.

---

