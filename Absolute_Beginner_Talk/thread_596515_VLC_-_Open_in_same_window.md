---
title: "VLC - Open in same window"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by stomponthis on 2007-10-29
Sorry this may be a silly question!~
VLC is my main video player, but I have a problem that i cant solve!
Every time I open a movie file it opens a new VLC app to play it, even if I have another VLC window already open?  Is there anyway to make it just use the one window? Oh, by the way I am opening the file from nautilis not from inside the app itself.
I have looked all through the preferences but havn't found anything!
HELP!

---

### Post by Pumalite on 2007-10-29
In VLC, go to File>Open File(choose your movie)

---

### Post by stomponthis on 2007-10-29
Thanks for the post :)
I know you can open a movie like that and have it open in the same window.
I was referring to opening it through nautilis.  I am sure when i used vlc in windows it would open new movies in the same app window that was already open!?

---

### Post by Alan McNea on 2007-12-03
I am not sure of the "CORRECT" way to do this I have spent several hours here and there looking for the answer you seek with no success.  So, I ended up writing a little shell script to do it for me.  It is not great but it works with what I am using. (xubuntu)

Basically all the script does is search for all the open occurances of 'wxvlc' and kills them passing a "kill $PID" command, then it simply opens a new call to wxvlc.

In order to make the script work from the gui, you will have do something along the lines of.  Right click on the media file, select "Open With/Open With other Application" then choose to open the file using a command line argument this might be called something like "use a custom command".  Anyway once you find that box, paste this into it "rvlc %F" minus the quotes of course. (Not sure if that paste line will work for all Windows Managers, I am xfce)

Ohh, yah place rvlc in you /bin/ or some other equivilant directory.

In case you don't know how to make a script, just simply copy the text below into a text editor and save it as "rvlc" minus the quotes.  Next you will need to move the file to  /bin/ and you will have to make sure the permissions are correct.  You can use the other files in that directory for a model of what the permissions should be or you can just type  "chmod 777 /bin/rvlc" (minus quotes) and that will set the permissions.  P.S. you might need to throw a sudo before that chmod.

alright here is the rvlc file:
#!/bin/sh

#FIND ALL OPEN VLC APPLICATIONS AND CLOSE THEM
##############################################
ps_info=$(ps ax | grep wxvlc | grep -v grep | sed 's/^ *//')
ps_id=${ps_info%% *}
while [ ${#ps_id} -gt 0 ]
do
  kill $ps_id
  ps_info=$(ps ax | grep wxvlc | grep -v grep | sed 's/^ *//')
  ps_id=${ps_info%% *}
done

#OPEN A NEW VLC
##############################################
if [ ${#1} -gt 0 ]; then
  wxvlc "$1" &
else
  wxvlc &
fi

---

