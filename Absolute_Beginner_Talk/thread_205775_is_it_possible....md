---
title: "is it possible..."
date: 2006-06-29
forum: Absolute Beginner Talk
---

### Post by MaximB on 2006-06-29
to delete the /home or the /root folders without behing or knowing the su password or the password of somone with outoreties on your computer ?
if not - what harmfull viruses could be made under linux ? (as you are not logged in as the "su" by default)

---

### Post by IYY on 2006-06-29
If a malicious user has physical acces to the machine, there's no way to stop him, no matter what operating system you use. If it's attacks over the internet you're concerned about, then no, it's not possible. In theory, it is possible to create Linux viruses using buffer overflows that will give root access, but it's much more difficult than on other operating systems and patches come out frequently to protect you from such attacks.

---

### Post by Kilz on 2006-06-29
[QUOTE=MAXDDARK]to delete the /home or the /root folders without behing or knowing the su password or the password of somone with outoreties on your computer ?
if not - what harmfull viruses could be made under linux ? (as you are not logged in as the "su" by default)[/QUOTE]

Sure pop in a windows restore disk and trun it, or take a windows boot floppy and type in format c: and hit enter. Viruses are not normaly a problem on Linux, it dosnt have the thousand + security holes that Windoz dose and its setup to be secure. All that open code and all the people looking at it tends to make them disapear fast.

---

### Post by MaximB on 2006-06-29
1.in ubuntu you are not logged as a su by default...what about other linux distrebutions ?
2.IYY - tell me more about your theory about viruses in linux...
3.IYY - I didn't meant of phisical acceess - I meant about viruses on the net
4.Kilz - I know that you can delete linux if you are logged into windows
but can u delete thuose folders in ubuntu not as su ?

---

### Post by MaximB on 2006-07-10
weeks have past...any answers ?

---

### Post by Brunellus on 2006-07-10
it's trivial to hose any computer that you have physical access to--use the bootable media of your choice, boot, and then destroy the partitions you want to destroy.  Not so easy to do remotely, of course...

I don't know much about buffer overflow/privilege escalation attacks, but yes, they are possible and do occur from time to time.  If you're really paranoid, I suggest you go talk to the OpenBSD guys... they tend to be obsessive about security like that.

---

### Post by Thiesen on 2006-07-10
I think what Maxddark is wondering about is if it's possible to hack a computer running Linux.

My answer is; it depends.

Take for example a totally newbie when it comes to any computer and tell him to play around with the computer. That person would have no clues of what he's doing. Add to that he's also gullible beyond belief so he happily falls for every kind of phishing attack and Nigerialetter out there. Such a person would be a obvious security risk.

And now take myself as an example. I'm a Windows user (but I'm in love with Ubuntu big time) and I'm a security minded person beyond belief (you can call me paranoid about security if you wish). I know what kind of webpages would wreck havoc on my Windows system (pr0n sites and warez sites, I know where to get both elsewhere). I have so far yet to get any adware, spyware, trojans and viruses unknowingly on my Windows system. The few times I've had one of those I knew what I was doing and I also knew what to do next.

Linux is built with security in mind (as every other Unix variant out there) and thus it would be very difficult to destroy a Linux system that easy. Ofcourse there's keyloggers even for Linux that can steal keystrokes the system administrator issues to get root access but a system administrator is unlikely to go to webpages known to harbour such keyloggers (Internet Explorer has no security checks, Firefox has) and therefore a Linux system wouldn't run such code without the consent of the user.

The only way you would be able to hack someone would be to use social engineering. And trust me, humans is known far and wide not to user their brains (more likely their nuts (if you're a male, if you're a woman... well... :-) )).

As for buffer overflows, you would be amazed to know what the concept of open source is all about. If you have the source code for a program you would correct the potential buffer overflows that you discover. That's called bug fixing. The whole linux world is filled with exactly these kind of persons that dedicate their lives to do bug fixing. That's why a potential buffer overflow get fixed in no time after it's been discovered. This isn't the case with the world of Windows (closed and proprietary code). It's a known fact among every programmer out there that the programmer that makes a program can't easily discover the flaws in his own program. They need others to discover the flaws for them. Therefore a potential buffer overflow in Microsofts software can lay dorment for very long periods of time without being discovered (MSBlaster and Sasser to name a few). Therefore it's extremely difficult to make an exploit for a Linux system.

Btw, I like long posts... :-)

---

