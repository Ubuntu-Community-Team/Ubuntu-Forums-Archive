---
title: "[SOLVED] phpBB"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by RadiationHazard on 2008-01-27
Ok, so I have posted something on this before but everything was messed up because i'd done everything wrong. But everything is working great now!! so now what i need to know how to do is what i need to put into these boxes.

ps. when i get this working i plan on making a how to on this. because i've had a really hard time with this and i think it could help people.

---

### Post by emarkd on 2008-01-27
So I take it you got phpmyadmin working?  If so, you'd:

1. log in to phpmyadmin with the root account and select privileges.
2. scroll down a bit and select Add new user
3. give it a username and password and the easiest thing to do is tell it to create a new database for the user with the same name.

Now you just tell phpbb what you just did:

The server is localhost
The username and database are the same thing - whatever you told it to use
The password is whatever you told it
The prefix is fine; you can leave it alone.

Maybe your long process is almost at an end :)

---

### Post by RadiationHazard on 2008-01-27
so in the screen shots below is everything done the way it's supposed to be?

---

### Post by emarkd on 2008-01-27
Close - The host is just localhost.  I think the box there drops down and has that as an option instead of "Use text field".  Also in the "Database for user" section, tick the "Create database with same name and grant all privileges" button.

---

### Post by RadiationHazard on 2008-01-27
Ok, i think i fixed everything that you were telling me to correctly?
tell me if i did.
and also there are multiple options in the drop down box, which on should i chose?

ps. thank you for all your help!

---

### Post by emarkd on 2008-01-27
In the Host dropdown box, select localhost and remove the text from the text field there.

I can't tell you if you did because I can't see what you're doing ;)

You're welcome for the help

---

### Post by emarkd on 2008-01-27
Now I see your screenshot.  Just select Local from that dropdown and you should have it

---

### Post by RadiationHazard on 2008-01-27
alright!! phpbb is up and running!! =D
now can i get a quick tut on how to use it? xD 
haha i'll get it after i play with it for awhile but i'd like to know how to create registroy so people can login how to create the forums because i just tried and it didn't work. =[
i would also like to know where i can get themes for phpbb and how to use the themes.
i would like a black and red theme if you know where a nice looking on is.

---

### Post by emarkd on 2008-01-27
Actually, I can't help you with any of that!  I've never used it before.  But I'm very glad that we got it up and going.  I suggest that you hunt out a phpbb forum somewhere and search around there.  I would hope that phpbb has a bulletin board on their web page :)

Anyway, enjoy your new software.

---

### Post by RadiationHazard on 2008-01-27
Ok, well thank you SOOOOO much!!
I've been trying to get that for days!

-RadiationHazard

---

### Post by emarkd on 2008-01-27
You're welcome.  Glad I could help.

---

