---
title: "Restricting Access: Can I do this?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by KelliShaver on 2007-10-15
Hi, folks.

I've used Ubuntu on my laptop for a while, but never anything more than the default install, really. It's an old laptop that I just use for writing and surfing the net, so there was never a need for any real sort of customization.

Now, however, I'm looking at redoing my daughter's computer, which is currently running Windows XP I haven't been happy with the level access restriction that XP provides. I can secure/hide most things I don't want her getting into (operating system files, program files, etc.) from her user account, but it also makes it a pain for me to get to them even from my administrator account.

My daughter's reads very well and is pretty computer savvy for her age (5.5), but part of that is due to her desire to experiment, and as such, I find myself reformatting, reinstalling, and fixing her computer a lot.

What I'm wondering is, is it possible to install Ubuntu on her computer and set up an account for her with the following access privileges?

- Use FireFox to visit a restricted list of sites (say, maybe only ones I have bookmarked)
- Use The GIMP or other paint program
- Use AbiWord or OO, or even just a basic text editor. I mean, she's 5, after all.
- The ability to create/save/edit/delete her own documents
- Read-only access to music
- I want to keep her from accessing/modifying anything else on the system.

Primarily what she uses the computer for is to play flash-based games online (reading and math games, etc.) and to do artwork. Restricting access to the sites she's able to visit isn't a big issue, since the computer is in the living room and we monitor her activity on it, but if it's doable, it would just be one more nice thing to have.

So, all that said, would it be possible to set up an account for her with something approximating those access restrictions, and if so, what would I need to do to get started?

I'm pretty comfortable using and working with linux. I understand the file system well and have done some minor tweaks and customizations to various distros here and there throughout the years. It doesn't bother me to have to dig deep into system files and config settings. I've just never dealt with setting up a kid-friendly, restricted account before, so I'm not really sure where to begin.

**Edit:** It looks like I can use Glubble for restricting access in FireFox. [http://www.glubble.com/](http://www.glubble.com/)

Thanks!

---

### Post by Pumalite on 2007-10-15
[http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/](http://ubuntu-tutorials.com/2007/10/06/limiting-access-to-websitesdirectories-with-htaccess/)
[http://www.mail-archive.com/dubailug@yahoogroups.com/msg02723.html](http://www.mail-archive.com/dubailug@yahoogroups.com/msg02723.html)
[http://osdir.com/ml/mail.cgatepro.general/2004-07/msg00543.html](http://osdir.com/ml/mail.cgatepro.general/2004-07/msg00543.html)

---

### Post by twiceasworn on 2007-10-15
Those three links should point you in the right direction.  I just wanted to say that you came to the right operating system for user restriction :)

---

### Post by KelliShaver on 2007-10-15
Thanks, guys. :)

---

### Post by Keith_Burton on 2007-10-15
For the other things besides the Firefox restrictions I'd:

Install Ubuntu using your own name for the account, not hers. Use a password that's beyond her capabilities to guess.

After it's installed and everything's working, add your daughter's account. She won't be able to use sudo, adding some additional protection.

Edit the menu on her desktop, removing all the programs you don't want.

From your account, use sudo mode to put the music folder (or a link to it) on her desktop. Set yourself as the owner. Set the permissions on the folder (and all files and subdirectories beneath it) to Owner-read/write, Group-read-only, Other-read-only.

You said you were experienced so I didn't go into detail on how to do each of these tasks. Post again if you need more information on how to accomplish any of them.

You might also want to take a look at Edubuntu, which includes plenty of kid's software.

---

### Post by KelliShaver on 2007-10-15
I hadn't even thought about EdUbuntu, not sure, why... it just never corssed my mind. That's a great idea. Thanks!

> From your account, use sudo mode to put the music folder (or a link to it) on her desktop.

this is the only part I'm not clear on (though I can always look it up), since I've never had a need for multiple accounts before. The rest makes great sense, though. Thanks. :)

---

### Post by KelliShaver on 2007-10-16
I just wanted to come back and say thanks to everyone for the help. I have the computer set up now running edubuntu, with a lot of educational software and games installed. I've hidden and restricted access to everything I don't want her messing with and given her read-only access to the music folder.

Glubble, as it turns out, is a bit buggy in linux, so for now, I've just created her bookmarks and a custom start page, then went into the chrome CSS file for FireFox and hid all the menus and address bars, etc. so she can't enter other URLs. If I need to do something more secure later, I will. It's not really a security issue, though, since she's 5 and well-supervised. I mainly just wanted to make the interface easier for her. So that solves the browsing issue well enough for now.

It was much quicker and easier than trying to kid-proof XP, that's for sure. 

She was very excited to see all of the new software going on there for her to explore tomorrow.

---

### Post by Pinger05 on 2007-10-16
This is an awesome thread.  I think every parent who has a kid that uses the internet should read it.

Just my two cents worth.

---

