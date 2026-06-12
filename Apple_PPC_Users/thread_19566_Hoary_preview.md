---
title: "Hoary preview"
date: 2005-03-12
forum: Apple PPC Users
---

### Post by Ptero-4 on 2005-03-12
Hi. I wanted to know. Is the hoary install CD that was just released the final release of Hoary, or is it a beta/RC version of hoary.

Thanks

---

### Post by bored2k on 2005-03-12
[QUOTE=Ptero-4]Hi. I wanted to know. Is the hoary install CD that was just released the final release of Hoary, or is it a beta/RC version of hoary.

Thanks[/QUOTE]
 Preview disc. Not final.

It's amazingly stable though! I have only counted 2 problems this one has that Warty final doesnt. It fixed some Warty errors I had also.

---

### Post by DJ_Max on 2005-03-12
[QUOTE=bored2k]Preview disc. Not final.

It's amazingly stable though! I have only counted 2 problems this one has that Warty final doesnt. It fixed some Warty errors I had also.[/QUOTE]
I agree, I have the Alpha version, and experienced a few problems, which there was either a work around, or update for.

---

### Post by bored2k on 2005-03-12
[QUOTE=DJ_Max]I agree, I have the Alpha version, and experienced a few problems, which there was either a work around, or update for.[/QUOTE]
 It's running very good here compared to how the 1st Ubuntu Warty Release Candidate screwd up my sound/system overall [and computers I had installed it on at school at the time.]

---

### Post by Ptero-4 on 2005-03-12
[QUOTE=bored2k]It's running very good here compared to how the 1st Ubuntu Warty Release Candidate screwd up my sound/system overall [and computers I had installed it on at school at the time.][/QUOTE]
 Thanks. And Does someone have a good web hosting. 'cause I got the mol kmod sittin' in a CD but since I don't have web hosting I can't post them. If anyone of you have hosting just send me a mail to [email]Ptero.4@gmail.com[/email] and I will send you the mol-kmods so that they can finally be accesible to all the ubuntu community (And be prepared 'cause as soon as I get hoary I'm going after the kmods for the hoary kernel).

Thanks and hope to have some place to upload those kmods.

P.D: I got 50 gmail invites laying around if anyone wants (but remember hotmail rejects gmail invites and yahoo throws them to the bulk folder).

---

### Post by Achille on 2005-03-13
I have just a stupid question: I have just done a fresh installation of Ubuntu with the preview CD of Hoary. When the official Hoary will be released, will my installation be automatically updated to the stable version with Synaptic or should I do a fresh installation again?

---

### Post by jimmt on 2005-03-13
[QUOTE=Achille]I have just a stupid question: I have just done a fresh installation of Ubuntu with the preview CD of Hoary. When the official Hoary will be released, will my installation be automatically updated to the stable version with Synaptic or should I do a fresh installation again?[/QUOTE]

They have an updater now that will check for updates. Pretty nice and is simular to Suse and Microsoft update, meaning, you will have an "update" icon on you task bar showing you updates are ready to install. 

Also, you can always run Synoptic and do "Mark Update All" and do a smart update to update you system to current build including all applications that you have downloaded from Synoptic prior to the build -- if updates are available. 

Have to love Debian based systems :)

Jim

---

### Post by kris kincaid on 2005-03-13
I am on dial up. Can I download the install CD on a broadband connection, then use that to update? If so, how would you do that?

Thanks!

---

### Post by meyerm on 2005-03-13
Hi,

a new preview - very fine :-) So, did anybody test the image on a pegasos2? I already tried older ones but they all got problems when it comes to initalize the VGA so I can't even see if there are any error messages ;-)

Thank you

Marcel

---

### Post by kanem on 2005-03-13
[QUOTE=kris kincaid]I am on dial up. Can I download the install CD on a broadband connection, then use that to update? If so, how would you do that?

Thanks![/QUOTE]
After the CD is inserted and mounted a pop-up should pop up saying something like 'installation CD detected, do you want to upgrade from CD?'

If for some reason that doesn't happen, you can still add the CD to your sources.list file manually.

---

### Post by farruinn on 2005-03-13
[QUOTE=kanem]After the CD is inserted and mounted a pop-up should pop up saying something like 'installation CD detected, do you want to upgrade from CD?'[/QUOTE]

Are you sure that would work?  This is what I have in my /etc/apt/sources.list:

deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Preview powerpc Binary-1 (20050310)]/ hoary main restricted

You will have to run 'apt-cdrom add', then insert the disc and apt will add the correct line to your /etc/apt/sources.list.  I took a quick look at synaptic to see if it's possible to automate it there, but Hoary's version of synaptic is very different from warty's in terms of the sources.list dialog.

-Nathan

---

### Post by trash on 2005-03-13
Originally I dist-upgrade from warty to hoary(without a hitch).
I then broke my system again lol... Just installed the preview hoary and WOW!

The install only had one real issue, after the install type 'install video=ofonly' (G4,466)

Xorg needed tweaking, I added;

Section Module:

Load "GLcore"
Load "v4l"
Load "xtt"

Section "device"

Driver "r128" #"ati"
Option "UseFBDev" "true"

Also during the install I selected 'ca' for Canada which gave me French keyboard... no brob, i just selected 'US' as default in gnome. It did however detect my USB keyboard as a 'microsoft' instead of a macintosh, which i also switch through gnome(which did complain of issues, but all works fine).

---

### Post by DJ_Max on 2005-03-13
[QUOTE=Ptero-4]Thanks. And Does someone have a good web hosting. 'cause I got the mol kmod sittin' in a CD but since I don't have web hosting I can't post them. If anyone of you have hosting just send me a mail to [email]Ptero.4@gmail.com[/email] and I will send you the mol-kmods so that they can finally be accesible to all the ubuntu community (And be prepared 'cause as soon as I get hoary I'm going after the kmods for the hoary kernel).

Thanks and hope to have some place to upload those kmods.

P.D: I got 50 gmail invites laying around if anyone wants (but remember hotmail rejects gmail invites and yahoo throws them to the bulk folder).[/QUOTE]
Yeah, I got can host you. How big is the file? The server is in Texas, at The Planet, so it's good bandwidth. PM me, I can set you up ASAP.

---

### Post by Ptero-4 on 2005-03-13
[QUOTE=DJ_Max]Yeah, I got can host you. How big is the file? The server is in Texas, at The Planet, so it's good bandwidth. PM me, I can set you up ASAP.[/QUOTE]
 It's 36k. probably will work.

---

### Post by DJ_Max on 2005-03-13
[QUOTE=Ptero-4]It's 36k. probably will work.[/QUOTE]
 Info sent!

---

