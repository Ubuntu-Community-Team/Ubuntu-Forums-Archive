---
title: "A real secure password manager pleaze?"
date: 2007-09-08
forum: Absolute Beginner Talk
---

### Post by Baarhisveiki on 2007-09-08
Hi,
I am looking for a good password manager and on one of the threads here i found a link to the Revelation site. Apparantly a well known password manager for linux 

BUT at the bottom of that page i read this statement :


[COLOR="Red"]Security warning: when Revelation is running
        and has opened a data file, both the file contents and the
        file password are stored in memory as plaintext. The root user
        or other programs on your computer may be able to access this
        data. This is unfortunate, but it is hard to avoid, and a
        problem Revelation shares with most other applications of this
        type.



        Please only use Revelation on your own computers, and take
        normal security precautions such as keeping your software
        updated and using a firewall.[/COLOR]

[COLOR="Black"]Now this is honest talking from their developers. But then again; is there a password manager who doesnt store this "problem"?:popcorn:[/COLOR]

---

### Post by ORBiTrus on 2007-09-08
> **Baarhisveiki said:**
> Hi,
I am looking for a good password manager and on one of the threads here i found a link to the Revelation site. Apparantly a well known password manager for linux 

BUT at the bottom of that page i read this statement :


[COLOR="Red"]Security warning: when Revelation is running
        and has opened a data file, both the file contents and the
        file password are stored in memory as plaintext. The root user
        or other programs on your computer may be able to access this
        data. This is unfortunate, but it is hard to avoid, and a
        problem Revelation shares with most other applications of this
        type.



        Please only use Revelation on your own computers, and take
        normal security precautions such as keeping your software
        updated and using a firewall.[/COLOR]

[COLOR="Black"]Now this is honest talking from their developers. But the again; is there a password manager who doesnt store has this "problem"?:popcorn:[/COLOR]


The GPG stuff, at expense of using kernel space.  There is litterally no way to prevent this - if you can read it, it's gotta go into main memory unencrypted, where uid 0 can always read, and your programs [assuming you lack advanced functionality such as a trusted computing module] can read too.  If your only concern is that it stores the password in main memory, I'm afraid I don't know of something that doesn't (with the exception of the GPG stuff).

---

### Post by Baarhisveiki on 2007-09-08
[][LEFT]I will check that out. But on the other hand i only intend to use it on our family computer on which i am root and it has a firewall and since i have no secrets for my wife...Revelations should do the trick i suppose...... 
Its just we wanted to store our zillion passwords from all those accounts we used to scribe on a now well used piece of paper. Included homebanking and Paypal and the likes. 
So i guess if this problem is common we might aswel rely on our own common sense?
Or does anyone recommends otherwise?[/LEFT]

---

### Post by dwhitney67 on 2007-09-08
I think you worry too much.  I would concentrate more on securing your system from an outside intruder (closing of unnecessary ports, using a router as a firewall, etc.)

Some, if not most modern systems, provide a Memory Management Unit (MMU) that prevents one application from reading (or even stepping into) the memory space of another, regardless of the privileges of the user running the application.  That said, it is highly unlikely (if you follow the advice in paragraph 1) that anyone would be able to install a rogue application on your system.  And even if  it occurred, it would be unlikely that that application could "see" anything.

Reading a file on the HDD is a different story.  Consider placing any sensitive files you have on a USB thumb drive.  Also consider encrypting the file; but in my opinion, this is overkill for the average Joe.

---

### Post by Baarhisveiki on 2007-09-08
Thanx for the feedback! i guess we can consider this topic as closed then. And yes i tend to worry too much.... . thats another topic but not for this thread.:KS

---

### Post by russell.h on 2007-09-08
Another thing to consider is that most reasonable passwords are less than 20 characters. That will mean that it will take up something on the order of 20 bytes in memory. If your computer has 1 gigabyte of RAM then there can potentially be something like 1 billion bytes in memory at the same time. Figure in swap and you are talking about a hell of a lot of data to sift through to find a password. Its not impossible (both windows media DRM and Apples "Fair"Play DRM I believe have been broken by finding decryption keys in the memory), but it would take more than just a casual inspection to figure out your password.

Plus, even if some program dumped your entire memory, in order to send it back via the internet (we are talking about some sort of remote attack here) they would have to upload a huge (like the size of your memory) file, which would take a hell of a long time. It might be possible to write an exploit that would automatically locate your password in memory, but I think I'm taking the paranoia a bit far here.

---

### Post by Chris S. on 2007-09-08
Or they could get their hands on some of the more popular password managers and dig through them to find the most likely offsets in process space that the passwords will be stored at.  Likewise for decryption keys.  Once you have the offset and the base address of the target memory, you can grab the password right away.  If there are patterns to finding the memory, a script could run on the victim's machine to automate the search.

But really, don't worry about things like this.  If your security is ever compromised, from outside or inside, it would be much easier for an attacker to set up a keylogger to feed keystrokes to his/her machine and get the plaintext of your username/password/loginsite, bypassing many of these security measures.

If you want better security, keep your passwords locked up in a desk drawer, or even better, your head.  Otherwise, the password manager is just fine.  It'll at least protect you from nosy people, which is going a long way in terms of security.

---

