---
title: "No Dice Installing umbutu 6.10! (EDGY THAT IS)"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by thehealing on 2007-03-07
I am really, really new to this format so bare with me.
P.S. I love ubuntu! Just need to work out the quirks!

Installtion wackiness:
So.  I have installed ubuntu twice because of: 1)when starting up, the picture on the screen is broken up/fragmented looking and  2) any time I would go into add/delete it would close before letting me add or remove anything.

Flash player Instillation problem:
I've tried soooo many tips on installing flash from the ubuntu forums but, to no avail.  The furthest I've gotten is having downloaded the flashplayer and  a folder shows up on the desktop.  What next?  I really need step by step HELP!!!

Ipod issues:
I have downloaded banshee ect. type programs to work with my nano.But,  haven't been able to convert the songs.  I get a error message.

P.S. The Ubuntu book is of no help, it is not specific enough.  I need a good explanation of each step.


:guitar: :confused: :guitar: :confused: :guitar: :confused: :guitar: :confused:

---

### Post by thehealing on 2007-03-07
P.S. I have a Power Mac g4. Could that be part of the problem's that I'm having?
:guitar: :confused: :guitar: :confused:

---

### Post by maniacmusician on 2007-03-07
no problem, good sir. Open a terminal, and navigate to the folder that was created. You do this by typing:

cd /home/[username]/path/to/folder

Once you're in that folder, you have to type the following commands:
> 
sudo mv libflashplayer.so /usr/lib/firefox/plugins
sudo mv flashplayer.xpt /usr/lib/firefox/plugins


What this command basically does is tell the computer to move (mv) the files (libflashplayer.so and flashplayer.xpt) to the folder located at /usr/lib/firefox/plugins. the "sudo" part is for administrative priveleges. it tells the computer "hey, run this following command (the mv command) as a super-user".

---

### Post by maniacmusician on 2007-03-07
Yeah, the PPC thing could definitely be part of your problem. PPC processor support was just phased out by Ubuntu, and Edgy is the last release that even supports it. I don't know if Flash works under PPC; probably not.

---

### Post by Kateikyoushi on 2007-03-07
Partially yes, there is no flash for PPC ie G4.
I would recommend to use synaptic to install software. System > administration > synaptic.
There is a Apple ppc forum look for more infrmation there.

This might be a good read, how to install anything in ubuntu. [LINK]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by thehealing on 2007-03-07
Thank you for responding.
I have tried to enter "cd /home/[username]/path/to/folder" into the terminal but it gives me this message "No such file or directory". 
Any ideas?

:( :guitar:

---

### Post by Kateikyoushi on 2007-03-07
cd is the terminal command to change directory, your home directory is located in /home/USERNAME where username is the username you entered during installation. /path/to/folder is used to refer to typing the path to the folder. In terminal you can alays use tab to autocomplete the path or commands.

I recommend to read the guide I post before because installing software from the ubuntu repositories via synaptic is much easier than to install manually not mentioning from source.

---

### Post by thehealing on 2007-03-07
Again thanks for the response.  Should I:guitar: :confused:  go to the repositories and try to install flash there?

:confused: :guitar:

---

### Post by Kateikyoushi on 2007-03-07
I wrote before that there is no flash for PPC all you can do is sign this. [LINK]("http://www.petitiononline.com/fla4lppc/")

---

### Post by thehealing on 2007-03-07
Well I signed the petition.  Whats next.  Get a pc?  What's your take?

:guitar:

---

### Post by Kateikyoushi on 2007-03-07
Well actually we did that but not because of flash, it was too heavy for my girlfriend, otherwise G4 was a really well built powerbook.

If it were me I could live without flash, actually I do not have it installed on my PC either.

To install other software check synaptic there are some really cool players like the banshee.
This page can help with enabling repositories, and has a guide about installing software as well. [LINK]("http://www.psychocats.net/ubuntu/sources")

There is also a Apple ppc part in the forum which worth checking.

---

### Post by rocknrolf77 on 2007-03-07
A pc with lot's of intel hardware because of the open drivers, and maybe a nvidia gpu if your'e planning some gaming in the future. :) How old is your comp? Or maybe an intel based mac if you like them the best, and can afford one of course. I think they're to expensive.

---

### Post by thehealing on 2007-03-07
I believe my computer is a 96 or 97.  it's a hand me down from my dad.
What does "intel" entail?

I need flash player for our band to network on myspace, post videos of us ect.
What do I do.  Sony laptop?  Dell laptop?

:guitar: :guitar:

---

### Post by Kateikyoushi on 2007-03-07
Intel is a company mostly know for it's CPUs they control most of the PC market your Mac uses a g4 PowerPC cpu from IBM which didn't get so much support from developers due to the little 3% marketshare of Apple and very few people moved to linux from OSX so PPC isn't very well supported.

You could dualboot with OSX for example.

---

### Post by thehealing on 2007-03-07
Thanks!  I appreciate your feedback.
i am get os x.  A dual boot sounds good.
thanks again.

:) :guitar:

---

