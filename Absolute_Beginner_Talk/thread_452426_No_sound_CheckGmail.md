---
title: "No sound CheckGmail"
date: 2007-05-23
forum: Absolute Beginner Talk
---

### Post by smoaky on 2007-05-23
Have checkgmail mail running  and added this command to execute on new mail.
"play /usr/share/sounds/phone.wav" I do not get any sound when a new email arrives. I get the pop up box that alerts me I have new mail but no sound that I have added. :(
Any clues?
Thank you

---

### Post by shanepardue on 2007-05-23
Run Checkgmail from the command line and see what it says when you get a new mail. It should give you an error message. Also, make sure "sox" is installed..that is what the "play" command uses to play sounds.

---

### Post by smoaky on 2007-05-23
Hi shanepardue,
Great info !!
I Installed sox. I only get an audio alert to new messages when I re-boot and log-on. Logging off then back on does not activate and audio alert to new emails.
Do you want me to disable Checkgmail from start-up and then run Checkgmail from command?
what is the command line for doing that in terminal?
Thank you

---

### Post by shanepardue on 2007-05-23
yeah, disable it from startup and type "checkgmail" in the terminal and it should work..then send yourself an email to test the alert.

---

### Post by smoaky on 2007-05-23
OK did all that and ran it from terminal,sent myself a new message..got the pop-up with my new email alert  box but no sound still. HMMMMM  Only get a audio alert upon boot up and log on.
Rats!!!!

---

### Post by shanepardue on 2007-05-23
No error message in the terminal when you opened it that way? Are you sure you have the right location of the file in checkgmail's settings?

---

### Post by smoaky on 2007-05-23
Yes I did here it is:
Warning: Crypt::Simple not found ...

CheckGmail requires the above packages for password encryption
Please download and install from CPAN ([http://search.cpan.org](http://search.cpan.org)) if you want to use this feature ...

sox: Can't open output file '/dev/dsp': Device or resource busy


My command to execute on new email is  play /usr/share/sounds/phone.wav

---

