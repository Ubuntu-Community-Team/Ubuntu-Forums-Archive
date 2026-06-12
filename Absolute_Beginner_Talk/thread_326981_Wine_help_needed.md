---
title: "Wine help needed"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Paradoxed on 2006-12-28
Having reinstalled ubuntu and installed wine to run an app
SnetFone_Dialer_108.exe I used to use everyday without hassles, I have
come across a  slight annoyance.
The exe that I run takes me through an installation wizard and
thereafter I am able to launch the app and make a call. However now
there is only the install icon on the desktop. Previously after using
the app an icon was left on my desktop that I could simply click on to launchand now I have to always run through the wizard everytime to use the app..

---

### Post by deadgobby on 2006-12-28
Check out Wines FAQs or their live chat help
[http://www.winehq.com/site/irc](http://www.winehq.com/site/irc)
Gobby

---

### Post by Paradoxed on 2006-12-28
Thanks for the link but that does not help me in anyway.

ine version: 0.9.22 (odd considering I just installed it today)

So here is exactly what I do in the terminal

cd Desktop
Desktop$ wine SnetFone_Dialer_108.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:SetWindowTextA setting text "Preparing
\"SnetFone_Dialer_108\" package..." of other process window (nil)
should not use SendMessage

thereafter it starts with the installation wizard.
I click through the installation. I see this in the terminal

libGL warning: 3D driver claims to not support visual 0x4b
fixme:sfc:SfcIsFileProtected ((nil), L"c:\\Program Files\\SPT PC-Phone
Dialer\\sptskin.dll") stub
fixme:ole:ITypeInfo_fnRelease destroy child objects
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink

The last step asks whether I want to launch the dialer. This I do and
can make crystal clear calls. 

All I want to be able to do is avoid having to go through the installation everytime I want to use the application.

---

### Post by Paradoxed on 2006-12-28
Thanks for the link but that does not help me in anyway.

ine version: 0.9.22 (odd considering I just installed it today)

So here is exactly what I do in the terminal

cd Desktop
Desktop$ wine SnetFone_Dialer_108.exe
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
fixme:win:SetWindowTextA setting text "Preparing
\"SnetFone_Dialer_108\" package..." of other process window (nil)
should not use SendMessage

thereafter it starts with the installation wizard.
I click through the installation. I see this in the terminal

libGL warning: 3D driver claims to not support visual 0x4b
fixme:sfc:SfcIsFileProtected ((nil), L"c:\\Program Files\\SPT PC-Phone
Dialer\\sptskin.dll") stub
fixme:ole:ITypeInfo_fnRelease destroy child objects
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
libGL warning: 3D driver claims to not support visual 0x4b
err:menubuilder:ExtractFromICO Invalid ico file format
err:menubuilder:InvokeShellLinker failed to fork and exec wineshelllink

The last step asks whether I want to launch the dialer. This I do and
can make crystal clear calls. 

All I want to be able to do is avoid having to go through the installation everytime I want to use the application.](*,)

---

### Post by greyhill on 2006-12-28
Take a look in the /home/{username}/.wine/drive_c/Program Files/etc... and try to find the EXE file that is the program you actually want to run.  Then, create a new launcher on the desktop with the command ```
wine '/home/{username}/path/to/exe'
```

---

### Post by Paradoxed on 2006-12-28
thats what I was thinking of doing and trying to get to the file for the past 20 minutes.

this is what happens 

/.wine/drive_c$ cd Program Files
bash: cd: Program: No such file or directory

really confused now

---

### Post by christhemonkey on 2006-12-28
make that:
```
cd "Program Files" 
```
when in your ~/.wine/drive_c directory

The problem being it sees Program and Files as two seperate arguments.

---

### Post by Paradoxed on 2006-12-28
Wow thanks for the response. 

I have a feeling we are close to resolving this.

I now know that wine is a hidden folder under home

I tried to create a launcher and added the following in the Command:

wine '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe

now when I double click on the launcher on the desktop I get the following

Details: Text ended before matching quote was found for '. (The text was 'wine '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe

---

### Post by christhemonkey on 2006-12-28
The launcher needs to have this command:
```
wine '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe**'**
```
(note the ' that you missed off the end, otherwise it makes no sense)

---

### Post by Paradoxed on 2006-12-28
Chris thanks for your patience,

I created the launcher and entered this where it says command

wine '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe'

the icon appears on my desktop but nothing happens when I launch it?

---

### Post by christhemonkey on 2006-12-28
If you run that command from a terminal.
```

wine '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe'
 
```

What output does it produce?

Or does it launch the program?

---

### Post by Paradoxed on 2006-12-28
If I run the command in the terminal 


$ wine '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe'
wine: cannot find '/home/omega/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe'

---

### Post by christhemonkey on 2006-12-28
So that would be a no thats the wrong path....

Try this;

```
wine "/home/omega/.wine/drive_c/Program Files/SPT PC-Phone Dialer/msptfone.exe" 
```

And if that doesnt work try;
```
sudo updatedb
locate msptfone.exe 
```
to get the location of the executable.

---

### Post by Paradoxed on 2006-12-28
Ive attached a screen shot if it helps

---

### Post by christhemonkey on 2006-12-28
Are you sure your user name isnt steve?

```
wine "/home/steve/.wine/drive_c/Program Files/SPT PC-Phone Dialer/msptfone.exe" 
```

---

### Post by Paradoxed on 2006-12-28
Sorry Chris, yes the name is steve

so what I have tried thus far is to create a launcher with the below
wine "/home/steve/.wine/drive_c/Program Files/SPT PC-Phone Dialer/msptfone.exe"

and also 
wine "/home/steve/.wine/drive_c/"Program Files"/"SPT PC-Phone Dialer"/msptfone.exe"

in both instances no response from the icon.

I then did what you suggested

locate msptfone.exe
/home/steve/.wine/drive_c/Program Files/SPT PC-Phone Dialer/msptfone.exe

---

### Post by christhemonkey on 2006-12-28
Could you just run this from a terminal to make sure it works:
```
wine "/home/steve/.wine/drive_c/Program Files/SPT PC-Phone Dialer/msptfone.exe" 
```

---

### Post by Paradoxed on 2006-12-28
:-D 

Chris its all sorted!! Thank you ever so much. Once I ran the command from the terminal the application launched and immediately thereafter an icon appeared that I have just tested and it works magically. If you ever out in Vietnam/Thailand/Singapore give me a shout. I owe you

---

### Post by christhemonkey on 2006-12-28
No problem!

If your ever out in the north of England, give me at shout!


Talking of going out, im going to the pub.
Good night!!

---

