---
title: "New Custom Gnome Interactive Login"
date: 2009-05-11
forum: Art &amp; Design
---

### Post by garrynigel on 2009-05-11
hi,
Dis is my first serious project i wanted to work on linux..and i wanted to start with building a login screen
d login screen is gud but i wanted to make it more interactive
i mean when a user enters a name into the login username and den enters the password..if the password is correct i wanted to program the computer to give an audio output"Welcome  username"or watever..
So basically i wanted to build an interactive session between user and computer
Dis was an idea i had long back..initially i tht of recording a voice..but later on i realised there is the festival command in linux which makes the computer talk..watever u type..so the input of the username can be given to check with the database as well as an input to the festival command...
So i wanted to build dis out and den provide it for distribution on d forum or anywer...i need help as to wer i can easily refer to how the ubuntu login works and how to build it...
thank you
me an amateur....but would really love to learn.

---

### Post by Bölvaður on 2009-05-11
1. Install espeak

2. Put this into a file:
```
$ espeak -s 110 "welcome $(echo $USER). All hail $(echo $USER)"

```<added> make the file have executable rights ```
chmod u+x filename
``` </added>

3. place that file into /etc/init.d/

4.  Then make the script run at startup  (borrowed from [richardjennings]("http://ubuntuforums.org/member.php?u=237602"))
```
sudo update-rc.d whatever.sh defaults
```

Make sure other sound isn't using the audio card, so that means turning off all login sounds in system&#8594;preferences&#8594;sound

---

### Post by garrynigel on 2009-05-11
He thanx about espeak but im having a problem..iv typed the code dat u gave me in a file i created interentry and paced the code $ espeak "Welcome $(echo$USER)"
den i save it..now wen i try to execute the file using sh interentry it says $:not found

---

### Post by Bölvaður on 2009-05-11
if you give your user rights to execute the file it should be no trouble

if the file is on your desktop then
```

cd Desktop
chmod u+x filename
filename

```
to test it you can go system&#8594;preferences&#8594;sessions and add the path to the file, like "/home/garrynigel/Desktop/filename" and restart xserver, which is control + alt + backspace on 8.10 and below, but has to be activated in 9.04... there you can just log in and out.

---

### Post by garrynigel on 2009-05-12
hi der thanx for dat but its not comin i disabled the entire sound first and it dint come..den latr i went into sound tab and disabled the login sound ..in d  desktop..and the login sound actually came so im pretty sure the welcome thingy dint come
"update-rc.d: warning: /etc/init.d/interentry.sh missing LSB information"
wat is dis lsb information?
dat code dat u gave me to put in d file..i put the same code in d file and saved it in my home
den later i placed it in the init.d folderusing sudo cp interentry /etc/init.d/interentry.sh
now i did dis cos wen i tried the command sudo update-rc.d interentry.sh defaults...it was sayin d file is missin...
so  is der anyting im doin wrong..please guide...

---

### Post by Bölvaður on 2009-05-12
I have no idea.

Lets just take it slowly and first check if the command will do anything if you run it from the terminal. Did you get sound?


If so then we can try out having this only for your user.
Make a file on your desktop.
Write this code in that file.
Make it executable (either chmod or right click and change in properties)
System &#8594; Preferences &#8594; Sessions and add a new item on the list with the command same as the path to your file. You can copy your file and paste into the command... that gives correct path, but remember to delete the "file://"(leave the last /) thing at front.
Log out and log in again.

Did you get sound?


If so then I would suggest looking on the forums as clearly I am doing something wrong on how to set programs to auto start for all users.

---

### Post by garrynigel on 2009-05-12
he thanx maan it really worked....
now i wanted to build an entire theme based on dis..
have workd  extensively on gimp
iv got questions..
1.so i wanted to create a login screen along with dis interactivity setup and build  a new background and evryting..iv read somewer (dnt remember wer)dat gif images are not possible on d login screen so how do i make one....also wer do i look for studying dis..googled it but no help?
2.but as of now i have only one user how do i do it for all users?

thnx maan gr8 help

---

### Post by Bölvaður on 2009-05-12
[http://ubuntuforums.org/showthread.php?t=1151486](http://ubuntuforums.org/showthread.php?t=1151486)

making a gdm theme (login screen) is just making backgroun, few images for icons and setting them up in an xml file.

---

