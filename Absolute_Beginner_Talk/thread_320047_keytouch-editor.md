---
title: "keytouch-editor"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by Buck2348 on 2006-12-16
In keytouch-editor, how do I open the keyboard file I am using in keytouch?  The only option I can find is File --> Open, but I have no idea where the keyboard files are located.  Also, will the multi-media keys work only on players for which keytouch has a plug-in?  They are working now in rhythmbox, even though the keyboard I selected in keytouch does not list the keys, but they don't work for any other player.

Thank you,
Buck

---

### Post by Old Jimma on 2006-12-25
Hi Buck:

Try looking at [http://keytouch.sourceforge.net/dl-keyboards.php]("http://keytouch.sourceforge.net/dl-keyboards.php") to see whether your keyboard is listed. I think the files are located there.

I'm glad you got keytouch to work... Could you please let me know how to get keytouch to work? I installed from Synaptic...

Best regards,
Phil Smith
Duluth, GA

---

### Post by Buck2348 on 2006-12-26
> **Phil Smith said:**
> Hi Buck:

Try looking at [http://keytouch.sourceforge.net/dl-keyboards.php]("http://keytouch.sourceforge.net/dl-keyboards.php") to see whether your keyboard is listed. I think the files are located there.

I'm glad you got keytouch to work... Could you please let me know how to get keytouch to work? I installed from Synaptic...

Best regards,
Phil Smith
Duluth, GA
Hello, Phil:

Thanks for your reply.  I was able to find the keytouch keyboard files with a little searching--usr/share/keytouch/keyboards.  When I was playing around with it I deleted all the keyboard files except the one I'm using.  I also found the place to download a file for the keyboard I have, although it didn't work right out of the box.  It had a couple of keycodes duplicated and gave an error message as soon as I opened it with the keytouch editor.  That was fairly easy to fix, though.  

I don't know that I can tell you in detail how I got it to work.  If you'll post any difficulties you're having I'd be glad to try to help.  There were some annoyances.  One I remember was after editing a keyboard file in keytouch editor, keytouch wouldn't install it, saying that a newer version of the keyboard was already installed.  I think I got around that by directly editing the keyboard file with gedit and changing the name of it to something like MyKeyboard.  Another was after I deleted some keys from a file with keytouch editor, when I started keytouch it would give a warning separately for each key which had been deleted.  I think I got around that by renaming the keyboard inside the file too.  If you should need the scancode for a key you can get it by running "showkey" in a terminal.  That doesn't work in the normal gnome-terminal though--you have to go to a login terminal by hitting <control><alt><F1> and typing "showkey".  Each time you hit a key it will show the scan code in hexadecimal.  It shows another one when you release it.  To get out of there wait till it times out waiting for an input (about 10 seconds) and then hit <control><alt><F7>.  You probably won't need that though--keytouch editor is good at scanning the keys.  Its codes don't agree with the ones from *showkey* on the special keys anyway.  I've been trying to understand the scancodes for months and haven't got it yet.  The item keytouch calls keycodes seem to be somewhat arbitrary.  I just picked something that wasn't already used to change those duplicated codes.

As I said, let me know if I can help.

Regards,
Buck

---

### Post by Old Jimma on 2006-12-27
HI Bash:

I don't know how to start the keytouch program... I installed keytouch-editor from synaptic, the n looked for it under applications > system tools and other places under applications... it wasn't there! Then, I opened a terminal window (applications > terminal window), and typed "keytouch" and then "keytouch-editor". Neither started a program!

How did you get the program to start?? 

I think that once I get it to start, I can congigure my keyboard!

Thanks,
Phil Smith
Duluth, GA

---

### Post by Buck2348 on 2006-12-27
> **Phil Smith said:**
> HI Bash:

I don't know how to start the keytouch program... I installed keytouch-editor from synaptic, the n looked for it under applications > system tools and other places under applications... it wasn't there! Then, I opened a terminal window (applications > terminal window), and typed "keytouch" and then "keytouch-editor". Neither started a program!

How did you get the program to start??

Hmm...  In my installation they are both under System > Administration, but they will both also start from a terminal with the commands you used.  I assume you installed keytouch itself as well as keytouch-editor.  Did you look at the list in synaptic and verify that it shows them both installed?  (Check for the box at the left end of the listing being green.)  If that isn't right or you can't think of anything else to do you might try reinstalling.  I can't think of anything else right now.

Regards,
Buck

---

