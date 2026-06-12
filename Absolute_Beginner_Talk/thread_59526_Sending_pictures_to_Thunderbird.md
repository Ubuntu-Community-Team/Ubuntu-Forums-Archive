---
title: "Sending pictures to Thunderbird"
date: 2005-08-24
forum: Absolute Beginner Talk
---

### Post by vhaarr on 2005-08-24
Hi!

I just installed Ubuntu on my laptop and I'm missing some things that were convenient on Windows. Most of them have been fixed by my son, but some of them are too complicated for him to be any assistance.

One of those things is sending pictures to a new e-mail.

In Windows, I could select pictures in the explorer and right-click, choose Send To and "Mozilla Thunderbird". This launched TB, created a new e-mail and attached the selected pictures to it.

I see it is possible to send to Evolution, but I have no motivation for learning yet another e-mail client (and especially one that has more functions than my Swiss Army Knife.)

Is there any way to fix this? Don't feel compelled to write an answer in 100% detail, as I'm sure my son can help me figure this out if he gets some guidelines.

Thank you.

---

### Post by Lord Illidan on 2005-08-24
Open Thunderbird, begin a new message, and either => Insert => Image or Attach Image..very easy...

---

### Post by vhaarr on 2005-08-24
Yes, I'm aware that it's relatively simple to do it from Thunderbird, but thanks.

However, it's not what I want.

---

### Post by aysiu on 2005-08-24
[QUOTE=vhaarr]Yes, I'm aware that it's relatively simple to do it from Thunderbird, but thanks.

However, it's not what I want.[/QUOTE] I don't see why it's so difficult to just, when you're typing a new message, click "attach" and find the picture to email it. I mean, I get annoyed that I can't create a new launcher in Windows without having to actually locate the program, but that's the way Windows is. Each OS has its conveniences and inconveniences. I see a few options for you:

1. Stick with Windows
2. Learn Evolution
3. Attach pictures to your messages instead of expecting a "send this to Thunderbird" context menu. 

By the way, I'm in Windows XP right now, and I don't get that send to Thunderbird option in my context menu. How did you enable that?

---

### Post by vhaarr on 2005-08-25
I was told that the Ubuntu community was a very helpful one and that in contrast to some other help channels, they wouldn't go at you the instant you opened your mouth.

I didn't come here to be insulted, I came to get help.

[QUOTE=aysiu]By the way, I'm in Windows XP right now, and I don't get that send to Thunderbird option in my context menu. How did you enable that?[/QUOTE]

I have no idea .. I see now that I was mistaken in my original post, it's not called Send To and "Mozilla Thunderbird", but Send To -> "Email Recipient". Selecting some files and clicking this opens the compose dialog with subject "Emailing: <comma-separated list of files>" and a message body with some disclaimer in it.

---

### Post by ScoobyDan on 2005-08-25
vhaar,

Have you set Thunderbird as your default e-mail client? By default, Evolution is the preferred e-mail client, so you have to tell Ubuntu to use a different e-mail client if you want to send things to Thunderbird. Follow these instructions: [http://www.ubuntuguide.org/#changepreferredemailthunderbird](http://www.ubuntuguide.org/#changepreferredemailthunderbird) and see if that changes anything.

Unfortunately, I'm at work at the moment (on WinXP), so I can't check if this works, but it seems a good place to start.

Daniel

---

### Post by manicka on 2005-08-25
System-->Preferences-->Preferred Applications

change your preferred email reader to thunderbird

---

### Post by vhaarr on 2005-08-25
Hi!

I had already done this, and Thunderbird is the default e-mail client. I noticed, however, that the default "launch command" was "thunderbird -mail %s", so I tried setting it to only "thunderbird %s", but that didn't work either.

When I select files and pick Send To, it still uses Evolution.

Thanks for the help so far!

---

### Post by manicka on 2005-08-26
[QUOTE=vhaarr]Hi!

I had already done this, and Thunderbird is the default e-mail client. I noticed, however, that the default "launch command" was "thunderbird -mail %s", so I tried setting it to only "thunderbird %s", but that didn't work either.

When I select files and pick Send To, it still uses Evolution.

Thanks for the help so far![/QUOTE]

try the command

mozilla-thunderbird %s

 [http://www.majalah.com/#changepreferredemailthunderbird](http://www.majalah.com/#changepreferredemailthunderbird)

---

### Post by vhaarr on 2005-08-26
[QUOTE=manicka]try the command

mozilla-thunderbird %s

 [http://www.majalah.com/#changepreferredemailthunderbird](http://www.majalah.com/#changepreferredemailthunderbird)[/QUOTE]
 Ah, terribly sorry, "mozilla-thunderbird %s" was what I tried, of course.

---

### Post by joergenlie on 2006-08-27
Same thing for me. Can't manage to send pictures to thunderbird. I can do it with the TB sendto configuration in nautius, but that doesn't work if I select more than one picture. This is annoying](*,)  To attach one picture at the time is just not functionally a good solution. I want it simple. I can get it to work with evolution but i dont like evolution. Is the preffered applications configuration thing working properly? Isn't it this kind of problems it is ment to solve? 

Still hoping for some answers:-D  I belive in a solution


Jørgen Fredrikstad

---

### Post by vhaarr on 2006-08-27
I made a script to do this for me, using nautilus-sendto. I don't have it here, it is at my parents laptop, 4 hours drive from here, so I can't give it to you easily.

I will try to remember bringing it with me the next time I visit them.

---

### Post by grumpyone on 2008-06-18
Hi vhaarr

Did you ever solve this issue?  I, like you, cannot believe you cannot 'send to email recipient' from your Picture Folder.  That is the only thing so far that I have found frustrating with Ubuntu. 

Peace be with you.

---

### Post by ad_267 on 2008-06-18
This should just work by default now. Just right click on a picture and select send to then select Thunderbird if that's what you're using. Do you have Ubuntu 8.04?

---

