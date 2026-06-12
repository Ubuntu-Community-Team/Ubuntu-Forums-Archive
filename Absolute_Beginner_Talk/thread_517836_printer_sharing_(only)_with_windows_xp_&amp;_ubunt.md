---
title: "printer sharing (only) with windows xp &amp; ubuntu"
date: 2007-08-05
forum: Absolute Beginner Talk
---

### Post by lunaz on 2007-08-05
my setup:

main comp: windows xp/ubuntu dual boot, printer hooked up to this system.
other comp: ubuntu server with ubuntu-desktop (for roommate)

both ubuntu installs have user accts for me & my roommate, and i got CUPS printer sharing working between the ubuntus.

how would i get it working with windows + the ubuntu server?

any info needed? let me know.

---

### Post by Ozeuss on 2007-08-05
you'll need samba, or maybe a variant of it. once you set it up, it pretty easy to share printers.

---

### Post by lunaz on 2007-08-05
ok, but the printer is hooked up to the windows computer..

---

### Post by lunaz on 2007-08-05
update:

i've got the printer shared in windows xp, and i've got 'other print/network services' enabled from control panel>add win components. i went to the ubuntu comp & tried setting up a new printer with all the same names & descriptions as what i've got on this winxp/ubuntu comp.

i even added the same usernames & passwords to the winxp to match.

i alawys get the can't connect to cifs, trying agian error.

this is the guide i was trying.

[http://ubuntuforums.org/showthread.php?t=32190&highlight=samba+print+share](http://ubuntuforums.org/showthread.php?t=32190&highlight=samba+print+share)

if anything needs explaining/posted, let me know.

---

### Post by rbprogrammer on 2007-08-05
> **lunaz said:**
> my setup:

main comp: windows xp/ubuntu dual boot, printer hooked up to this system.
other comp: ubuntu server with ubuntu-desktop (for roommate)

both ubuntu installs have user accts for me & my roommate, and i got CUPS printer sharing working between the ubuntus.

how would i get it working with windows + the ubuntu server?

any info needed? let me know.

how did you get print sharing to happen?? i mean where did you find out how to set one up??

---

### Post by lunaz on 2007-08-06
for the ubuntu to  ubuntu installs i got to it in cups by going to [http://localhost:631](http://localhost:631) & publishing the printers, and adding my user accts.

havent' gotten it working in ubuntu/win yet.

---

### Post by Ozeuss on 2007-08-06
> **lunaz said:**
> update:
i've got the printer shared in windows xp, and i've got 'other print/network services' enabled from control panel>add win components. i went to the ubuntu comp & tried setting up a new printer with all the same names & descriptions as what i've got on this winxp/ubuntu comp.
i even added the same usernames & passwords to the winxp to match.
i alawys get the can't connect to cifs, trying agian error.
this is the guide i was trying.
[http://ubuntuforums.org/showthread.php?t=32190&highlight=samba+print+share](http://ubuntuforums.org/showthread.php?t=32190&highlight=samba+print+share)
if anything needs explaining/posted, let me know.

Are you sure you set up samba correctly?
did you complete the howto without problems?
does the printer URI start with smb://?
try using the winxp box's computer name ('homecomp' or whatever you named it) instead of an IP.

---

### Post by lunaz on 2007-08-06
where do i find a samba how to for what i want? and in plain english? :P

---

### Post by Ozeuss on 2007-08-07
> **lunaz said:**
> where do i find a samba how to for what i want? and in plain english? :P

the link you provided is good enough for setting up a printer. there are also several samba wiki pages. using samba for this issue worked for me, but note that you can also do this through cups, as explained for instance, [here]("http://linuxcrypt.net/?p=15")

---

### Post by lunaz on 2007-08-08
update:

i moved the printer to the ubuntu computer, got it working there using info from
[http://ubuntuforums.org/showthread.php?t=240282](http://ubuntuforums.org/showthread.php?t=240282)
and
[http://ubuntuforums.org/showthread.php?t=310450&highlight=headless+print+server](http://ubuntuforums.org/showthread.php?t=310450&highlight=headless+print+server)

but i still can't connect to it using windows comp. :(

---

### Post by pashashome on 2007-08-08
I did a search on connecting to a printer on Ubuntu from XP and followed the directions. I know that doesn't help you, but I do know that you do not need Samba installed to print from Windows to an Ubuntu printer. CUPS works quite nicely, if I remember correctly in my case I needed to use a PS driver on my Windows machine. That particular part wasn't abundantly clear in the guide I followed.  Using the regular Windows driver on the Windows machine would allow something to be sent to my Ubuntu machine, but it wouldn't print unit I changed the print driver to MS Publisher Imagesetter driver in my case. Hope some of that is helpfull.

---

### Post by lunaz on 2007-08-11
tyvm for that!
just adding oldpos <ip> to window's host file allowed me to network the printer!

i can now print over the network with either ubuntu or windows with [http://oldpos:631/printers/DeskJet-5740](http://oldpos:631/printers/DeskJet-5740)

there's just one problem left:

windows prints everything upside down and backwards, and no color... :(

---

