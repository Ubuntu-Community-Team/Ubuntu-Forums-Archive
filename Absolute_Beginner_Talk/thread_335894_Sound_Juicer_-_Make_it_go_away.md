---
title: "Sound Juicer - Make it go away"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by angelsneverdie on 2007-01-10
Allright.  I've changed it so that when i insert an audio cd rythymbox opens instead of sound juicer - but i can't figure out how to make it so that when i double click on the audio cd icon on my desktop it opens rythymbox instead of sound juicer - 
i don't want to remove sound juicer - i just don't want it to be the default anything.  when it comes to music i don't do a lot of ripping - i just want rythmbox to be the default.

anyone know how i can change what program opens when double clicking the icon?

Thanks!](*,)

---

### Post by ComplexNumber on 2007-01-10
right click on an mp3 or other audio file, go to 'properties', then 'open with'. click on the one that you want to open with by default.

---

### Post by angelsneverdie on 2007-01-10
i did that with my mp3 files - but there is no open with option for the audio disc icon - i want the cd to open with a diff. program

---

### Post by szf on 2007-01-10
Sound Juicer replaced cd-player as the default cd-player around Gnome 2.8, IIRC. Good luck in configuring your desktop your way in any event.

---

### Post by ComplexNumber on 2007-01-10
> **angelsneverdie said:**
> i did that with my mp3 files - but there is no open with option for the audio disc icon - i want the cd to open with a diff. program
in that case, go to main menu -> system -> preferences -> removable drives and media. then click on the multimedia tab. can i assume that when you insert some media in your cd drive, it does NOT automatically open up a program? this would be the case if you have the tick box UNTICKED (as shown in the screenshot highlight in red). if that were the case, that would allow you to double click the audio cd icon to bring up a program as specified (as shown in the screenshot highlight in pink)

---

### Post by angelsneverdie on 2007-01-10
Alright, let me see if i can explain better.

this is how everything is right now:
when i insert an audio cd, it automatically opens rythymbox
if i close the program and then double click on the audio disc icon it opens sound juicer
the checkbox you showed in your screenshot is checked, and the associated program is rythymbox

This is how i want things to work:
when i insert an audio cd, it automatically opens rythmbox
if i close the program and then double click on the audio disc icon it will open rythymbox


----
I tried unchecking the box, but it still opened with sound juicer when double clicking.
I wouldn't think that it would be too much to ask to be able to set whatever program you want as a default - so i'd like to think there is a way to do it . . . i may be wrong . . . but i hope i'm not.](*,)

---

### Post by ComplexNumber on 2007-01-10
>  This is how i want things to work:
when i insert an audio cd, it automatically opens rythmbox
if i close the program and then double click on the audio disc icon it will open rythymbox
then just change sound-juice to rhythmbox. 
note: i'm not quite sure if the "-d" switch will have the same effect on rhythmbox as it does on sound-juice, but according to the rules laid down by the freedesktop.org they should apply equally. let me know if it works or not.

---

### Post by angelsneverdie on 2007-01-11
i am not sure what you mean by 'change sound-juice to rhythmbox' - cange it where?
also the whole -d switch thing is way over my head, i'm a noob to linux - recently switched from windows.

---

### Post by ComplexNumber on 2007-01-11
> **angelsneverdie said:**
> i am not sure what you mean by 'change sound-juice to rhythmbox' - cange it where?
also the whole -d switch thing is way over my head, i'm a noob to linux - recently switched from windows.
i've just shown you in the screenshot. its circled in pink. you have to click on the tickbox before you can change it.

---

### Post by angelsneverdie on 2007-01-11
ok.  that.  I have already changed that to rythymbox . . but that seemingly only changes what happens when you first put in the cd - if the cd is already in the drive and i try to open it, it still opens sound juicer....maybe i should just give up and learn to live with sound juicer . .

---

### Post by ComplexNumber on 2007-01-11
hmmmmm yes, i see what you mean. last time i tried that it worked, but i was using fedora. i don't know if its ubuntu thing or a gnome thing.

---

### Post by angelsneverdie on 2007-01-11
as i said before, this doesn't seem like something that is too much to ask for . . is there an official suggestion box or something where i could suggest it be implimented in the next release?

thanks for trying to help me complexnumber!

---

### Post by ComplexNumber on 2007-01-11
> **angelsneverdie said:**
> as i said before, this doesn't seem like something that is too much to ask for . . is there an official suggestion box or something where i could suggest it be implimented in the next release?

thanks for trying to help me complexnumber!
i have the solution! i thought about looking through gconf-editor for any mention of sound juicer in there. go into gconf-editor, select Edit -> Find in the menu, type in "juicer", tick the 2 tickbox underneath where you have just typed in "juicer", then go to the part that is shown in the shcreenshot below. change that from sound-juicer to rhythmbox.
now click on the audio cd.

---

### Post by angelsneverdie on 2007-01-11
alright. . . i think you're on to something here.  here is what happens in the terminal window when i make the change to rhythmbox in the gconf-editor - it gives me this:

(gconf-editor:16719): GConf-CRITICAL **: gconf_entry_unref: assertion `REAL_ENTRY (entry)->refcount > 0' failed

when i double click on the disk it says:  Couldn't display "cdda:///dev/hdc".  There was an error launching the application.

any ideas?

---

### Post by rai4shu2 on 2007-01-11
Double-click on the entry titled "command" and enter this value into the box:

rhythmbox %s

---

### Post by angelsneverdie on 2007-01-11
See, i was just about to reply saying, "that's what i did"  but then i thought i might as well try it exactly word for word.  whadya know . . it works!!!!!!

thank you guys so much!  you rock:p :p

---

