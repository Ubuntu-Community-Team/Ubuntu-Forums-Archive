---
title: "Getting past EULA of application install agreement"
date: 2007-03-13
forum: Absolute Beginner Talk
---

### Post by Teleplayer on 2007-03-13
I have a problem that I don't think is specific to Ubuntu, but I am experiencing it on Ubuntu, so I figured this is probably a good place to ask my question.

I am installing the DivX codec on 6.10, and have d/l'd the archive from DivX, and extracted the contents.  I make sure that the "install.sh" can be executed, and launch it using "sudo ./install.sh".  I get the EULA, and when I reach the end it says "(END)" and will not prompt me to agree to the license conditions.  I can type ":" and follow with a "q", which give me control of the terminal again.

I have seen this happen once before on SUSE, but wasn't too concerned as the software I was installing didn't state that it could be used on that version of SUSE anyway.  Incidentally, a coworker of mine installed the same app on the same version of SUSE I was using today, and it worked for him, so since I have seen it on Ubuntu and SUSE I figure it is a Linux issue in general, and does't appear to have anything to do with versions of OS.

I have looked on this site as well as Google and have not found anything useful, so I am hoping that someone here can lead me in the right direction.

Thanks in advance,
Steve

---

### Post by lamalex on 2007-03-13
did you try typing yes? or .y or .yes?

---

### Post by Teleplayer on 2007-03-13
It won't accept input other than ":"... its as though it is hung.  I should have said that, too... I did try put in "Y", "y", and yes.  But, remember, it never gets to the question about agreeing (I can see what is "supposed" to happen in the install.sh file by viewing it in a text editor).

If I try to input any character other than the ":" I get an obnoxious beep.  The only other input that it will take is "Shift" which results in scrolling back up on the text.

Steve

---

### Post by Teleplayer on 2007-03-13
I got it... I hated to do it this way, but I removed the EULA section of the script.  Without it there, once I launched the script, I was immediately prompted to answer "yes" or "no"... wish I could have fixed it from the other direction (that is from the OS side, and not modifying the script).

Oh well, such is life.


Steve

---

