---
title: "How to disable passwords?"
date: 2006-09-18
forum: Absolute Beginner Talk
---

### Post by MasterTrave on 2006-09-18
Hi,

I am a complete NOOB when it comes to Linux.  I decided to dabble in it and heard that Ubuntu was a good Linux OS to us.  While flawed in some ways, I'm more or less impressed with it.  One of the many things that is bothering me is that it always hassles me for my username and password just to log in.  This is inconenient if you plan to use it as a common household computer.  It would be nice if there was a simple way to disable Ubuntu from always requiring that login information.  I see no such setting under the Administration menus.  Now remember, I'm a Linux NOOB, and anything other than a point-and-click method to solving this small trifle of a problem will be a major pain!

Thanks, and keep up the good work!  Looking forward to newer versions.

---

### Post by jd65pl on 2006-09-18
Goto:

SYSTEM>ADMIN>LOGIN WINDOW
[LIST]
[*]choose the secuirty tab 
[*]select enable automatic login 
[*]choose the account you want to autologin
[/LIST]

Thanks

J

---

### Post by MasterTrave on 2006-09-18
Wow, that was quick!

I'll give that a try.  Thank you for the help!

---

### Post by MetalMusicAddict on 2006-09-18
> **MasterTrave said:**
> Now remember, I'm a Linux NOOB, and anything other than a point-and-click method to solving this small trifle of a problem will be a major pain!
If this is your honest feeling and you have no willingness to learn, Ubuntu will not be for you. Linux is not a windows replacement.

Sincerely sorry.

---

### Post by Brunellus on 2006-09-18
Disabling passwords is an EXTREMELY bad idea.  The entire reason Linux is secure is because of the user/privileges design:  each user only gets as much access to the computer as he needs to get his work done.  The critical parts of the machine stay protected and off-limits.

Sure, you can disable this, but it's a massive step backwards.  

dugout canoes are easy to build and load because they are made of one hollowed-out volume that is easy to fill.  But when water fills this, the entire canoe sinks.

Modern cargo ships are very strong;  their hulls are made of a number of watertight compartments, whose bulkheads can be sealed.  A leak in any one of them doesn't mean the ship will sink:  the leaking compartment can be sealed off and the ship can still make it to port.

Of course, if you're used to paddling a canoe instead of sailing a large cargo ship, you could try opening all the bulkheads, or removing the doors--then you wouldn't need to worry about the compartments.  But when you puncture the hull, you'll sink--and, mercifully, in a lot less time than it woudl take you to watch *Titanic*

Users and privileges are your bulkheads.  Security threats are the raging sea.

---

### Post by MasterTrave on 2006-09-18
> **MetalMusicAddict said:**
> If this is your honest feeling and you have no willingness to learn, Ubuntu will not be for you.

I’m disappointed by the tone of your response, seeing as Ubuntu publicly calls itself “Linux for Human Beings”, and boasts being easy and hassle-free for newcomers.

I did admit that I am I NOOB to all this.  Give me a break!

---

### Post by jd65pl on 2006-09-18
But there should really be an issue with a computer that automatically logs on a user in an environment where the computer is not physically accessable by those looking to cause harm.

There should be no problem with doing this in a family home.

---

### Post by Brunellus on 2006-09-18
> **jd65pl said:**
> But there should really be an issue with a computer that automatically logs on a user in an environment where the computer is not physically accessable by those looking to cause harm.

There should be no problem with doing this in a family home.
the lack of passwords also goes for remote access as well.

---

### Post by MasterTrave on 2006-09-18
> **Brunellus said:**
> Users and privileges are your bulkheads.  Security threats are the raging sea.

You speak as if I have extremely precious and sensitive secrets that mustn’t fall into the wrong hands, or else all hope for mankind will be lost.

Come on, people!  All I want to do is use this on the extra family computer we happen to have.  In my particular case, a username and password procedure every time we turn the machine on just is not that critical!

Thanks for being good sports about this, and thanks again for your quick reply, jd65pl!

---

### Post by jd65pl on 2006-09-18
I have run SSH FTP and NFS on a machine which auto logs in and never have I been able to access the machine via any of these methods without having to give login details. Also the very fact that "remote login" is also disabled in the fore mentioned interface should also couteract the validity of this point, if it doesn't should I be questionning the security of one of my systems?

However I realise this digresses from the origal post

---

### Post by MetalMusicAddict on 2006-09-18
> **MasterTrave said:**
> I’m disappointed by the tone of your response
Im glad you can hear "tone" over the internet.
> **MetalMusicAddict said:**
> Sincerely sorry.
:)

---

### Post by paxmaniac on 2007-01-17
Come on, it's hardly an unreasonable request.

Since you can autologin a single user, why not have 'one click login' for multiple users?  You don't even need to disable the passwords internally (and certainly not for root).  

I'd like to be able to use Linux exclusively at home, and my three year old likes to play games on the web.  He can use a mouse, but not a keyboard (not very well anyway).  Click to login would be perfect!

---

### Post by viciouslime on 2007-01-17
This is possible with kubuntu, unfortunately it is still not possible for ubuntu without messing about with some files in /etc. This really should be an option in the greeter settings dialogue.

---

