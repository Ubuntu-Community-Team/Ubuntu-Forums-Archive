---
title: "Can't copy and paste from Terminal"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by ncb on 2007-07-27
Hi all,

I'm using Feisty Fawn.  I need to be able to copy text from the terminal (Gnome Terminal 2.18.0) and paste it into a text editor or other app, and it just "doesn't work".  I can highlight the text in the terminal, right click it (or use  Edit...Copy from the menu) and it just doesn't seem to go to the clipboard.  Copying and pasting in other application works fine.  And pasting into the terminal works fine.  Any ideas?  

Thanks for any help.

---

### Post by Mornedhel on 2007-07-27
Does Ctrl Shift C still work for copying ? Does the highlight-then-middle-click method work ?

---

### Post by ncb on 2007-07-27
Thanks for replying,

No, unfortunately, neither of those methods seem to work.  When I try to paste what I've tried to copy from the terminal window, all I get is whatever I last copied from a non-terminal window.

---

### Post by AlexenderReez on 2007-07-27
actually if right click and choose 'copy' suppose copy will work..... 
:)

---

### Post by ncb on 2007-07-27
No, right-click...Copy is the first thing I tried.  Just doesn't work.

---

### Post by AlexenderReez on 2007-07-27
> **ncb said:**
> No, right-click...Copy is the first thing I tried.  Just doesn't work.

i'm also a user:)

highlight some words and right click ,copy....paste...

---

### Post by Mornedhel on 2007-07-27
(He's tried that already.)

I'm using 2.18 too, I just tried Ctrl Shift C, Edit/Copy, Right click/Copy, and highlight/middle-click, and everything works fine. Googling various terms did not return anything meaningful. (Several complaints about ^C ^V but nothing like this.) Searching on the forum is worse (with all the suggestions of copy/pasting to/from a terminal...).

Bleh.

Does anyone *who has read the OP* have something on this ?

---

### Post by wpshooter on 2007-07-27
> **ncb said:**
> Hi all,

I'm using Feisty Fawn.  I need to be able to copy text from the terminal (Gnome Terminal 2.18.0) and paste it into a text editor or other app, and it just "doesn't work".  I can highlight the text in the terminal, right click it (or use  Edit...Copy from the menu) and it just doesn't seem to go to the clipboard.  Copying and pasting in other application works fine.  And pasting into the terminal works fine.  Any ideas?  

Thanks for any help.

Are you closing the terminal before you go to paste the copied material elsewhere.

If so, try leaving the terminal open while you do the paste operation.

Me thinks perhaps this is STILL a shortcoming in Ubuntu !!!

---

### Post by AlexenderReez on 2007-07-27
> **Mornedhel said:**
> (He's tried that already.)

I'm using 2.18 too, I just tried Ctrl Shift C, Edit/Copy, Right click/Copy, and highlight/middle-click, and everything works fine. Googling various terms did not return anything meaningful. (Several complaints about ^C ^V but nothing like this.) Searching on the forum is worse (with all the suggestions of copy/pasting to/from a terminal...).

Bleh.

Does anyone *who has read the OP* have something on this ?

it is not a matter of he tried it or not...it is a matter of i always copy from terminal by that ways :)

---

### Post by paradoc on 2007-07-27
If you highlight your text, Copy (Shft+ctrl +C) becomes available in 'edit'

perhaps you only forgot to highlight it?;)

---

### Post by ncb on 2007-07-27
Yes, thank you for replying.  I am not trying to be obtuse.

I understand that I'm supposed to highlight the text in the terminal window, right-click, and select Copy from the pop-up menu.  Alternatively I should be abe to select Edit...Copy from the menu, or press Ctrl-Shift-C.  None of these methods seems to place the highlighted text into the clipboard because when I go to paste it into a text editor, all that gets pasted is whatever I coped from any non-terminal window.

Does anyone know if there is a way to view the contents of the clipboard?  Thanks for any reply.

---

### Post by AlexenderReez on 2007-07-27
> **paradoc said:**
> If you highlight your text, Copy (Shft+ctrl +C) becomes available in 'edit'

perhaps you only forgot to highlight it?;)

hm...i can confirm this way is not work for copy from terminal...as mentioned by op :)

---

### Post by Mornedhel on 2007-07-27
GNOME does have a somewhat short-lived clipboard (for instance, I've painfully learned *never* to close SciTE before I paste something from it). If you don't close gnome-terminal before you paste though, I'm out of ideas (not that I had any to start with).

---

### Post by ncb on 2007-07-27
Thanks all.  You may not have the answer but you sure are responsive :)

FWIW I have been leaving the terminal window while trying to paste, and yes I have been highlighting the text. hmmmm, maybe I should try a different terminal than Gnome?  Any suggestions?

---

### Post by Mornedhel on 2007-07-27
I heard wonders about screen.

---

### Post by AlexenderReez on 2007-07-27
copy ,close terminal,open text editor ,paste also work:)

---

### Post by Mornedhel on 2007-07-27
I think we all understood it works for you, AlexenderReez.

Could you please pass on some awesomeness to ncb ? :P

---

### Post by paradoc on 2007-07-27
There seemed to be this sort of problem (copying to clipboard) a few months ago, especially from Open Office, but updates appear to have corrected this.  With a fully updated Feisty Fawn, (I'm sorry, Alexender!), it works fine for me (IMHO) as in #10 of this thread, so I'll stick to what I wrote pro tem...perhaps it'll be different tomorrow!

---

### Post by arron on 2007-07-27
Not sure why this hasent come up before, but click and drag the text to select, then middle click (or left and right at the same time) to paste it.  Old Unix thing that can be very quick between screens. This works in terminal only mode when the mouse is installed for terminal.

---

### Post by AlexenderReez on 2007-07-27
> **Mornedhel said:**
> I think we all understood it works for you, AlexenderReez.

Could you please pass on some awesomeness to ncb ? :P

haha..lol...ok take this--> :KS:KS:KS

actually i think if we want to answer something ,make sure we have done it,or works for us...that is way i want to prove it with screenshot :) ,don't just talk nonsense ,give instruction without try it , because op may has tried it....but if it work for other user,then there is something wrong with op manner :) ....

do you have install ubuntu-desktop meta-package?(in case if you have uninstalled it without realized it:) , check it )

also....

i have install gedit plugin (search in synpatic please:) ),and it provide many more option of text editor:)

---

### Post by ncb on 2007-07-27
OK, I updated my system, rebooted (which was almost certainly unnecessary), and the problem went away.  All the methods mentioned in this post that should allow me to Copy from the terminal now seem to work.

I don't need anyone to mention that I should have tried this before posting in the first place, but I understand if you just can't help yourselves :)

Thanks everyone.

---

