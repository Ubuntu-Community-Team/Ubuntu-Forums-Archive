---
title: "Trouble with Password in Terminal"
date: 2006-06-23
forum: Absolute Beginner Talk
---

### Post by petgraveyard on 2006-06-23
I have tried to use the script located here - [http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntu:Chronicles#Install_Firefox_1.5)
to install the newest version of Firefox on my brand new install of Ubuntu.  However, the script asks me for the password, as do other commands I try in the terminal.  I try to type in my admin password, but I cannot type where the cursor is blinking (nothing happens when I press the keys).  I am able to type if I press enter and then type, but when I enter my password then it says that it is incorrect.  Does anyone know how I can enter my password in the terminal?  Thanks in advance!

---

### Post by hotbrainz on 2006-06-23
TRY 

> sudo -s

then u get admin priveleges until you close the konsole and so it wont ask you for the password. Problem solved :) iguess

---

### Post by Fass on 2006-06-23
The terminal does not give feedback when you type in a password. The password line is blank and "nothing happens" on it by default when you enter passwords - that's what's supposed to happen. You won't get "Password: *******" when you enter it, you'll get "Password: [blank]" no matter what you enter. So, do not fret, just enter your password and press enter.

---

### Post by hotbrainz on 2006-06-23
Sorry never thought of that. Me trying to be clever and all.
Cheers Fass

---

### Post by Fass on 2006-06-23
I try not to be too condescending in these replies, but one does have to remember that the forum is "Absolute Beginner Talk" and thus one has to remember to think of the basics. :)

---

### Post by bruce89 on 2006-06-23
The version of firefox in Ubuntu 6.06 is the same as mozilla's version, so why are you doing that?  That guide is aimed at Breezy (5.10)

---

### Post by petgraveyard on 2006-06-23
Well, I did it because the native version of Firefox is 1.5.0.3 and the current version is 1.5.0.4.  Also, I wanted a clean install of Firefox seperate from the native.

---

