---
title: "Where is this file?"
date: 2006-05-02
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-05-02
From the Unofficial Ubuntu website, I "installed" the script to change the background wallpaper.

It said to put the images in ~/.backgrounds which is hidden directory. I have Nautilis set to show hidden dirs, but can't find the "backgrounds". I looked in / but there is no backgrounds directory.

Help!!!


this is the set-up from the webpage:
[http://easylinux.info/wiki/Ubuntu#How_to_set_up_automatic_background_change_.28GNOME.29](http://easylinux.info/wiki/Ubuntu#How_to_set_up_automatic_background_change_.28GNOME.29)

 How to set up automatic background change (GNOME)

mkdir ~/.backgrounds
cd ~/.backgrounds
wget -c [http://easylinux.info/uploads/change_background.py](http://easylinux.info/uploads/change_background.py)
chmod +x change_background.py

    * To change desktop background every time you reboot your computer 

export EDITOR=gedit && crontab -e

    * Add the following line at the end of file 

@reboot ~/.backgrounds/change_background.py

    * ~/.backgrounds is hidden directory, see #How to show all hidden files/folders in Nautilus
    * Copy images you wish to see on your background to ~/.backgrounds directory

---

### Post by gabruo on 2006-05-02
~ is your home directory for the current user.  Have you looked in there?  Hope I am not stating what is obvious to you,

---

### Post by jazzmuzik on 2006-05-02
Any file or directory that begins with a period (.) is "hidden" from normal view. You can still view and access it, but you have to turn on that ability as you found out. The tilde character (~) represents your user directory, which is located here: /home/(loginName)

What those instructions don't tell you is you need to open up the Terminal program (Applications, Accessories, Terminal). The terminal program automatically starts in your user (home) directory. Then at command line type each line by itself and press enter:

(But first a little info about cutting and pasting in Linux. Just highlight any text with the left mouse button and it is automatically copied to the clipboard. Press the middle mouse button and you can paste it. So try copying and pasting one command at a time below into the Terminal program.)

mkdir ~/.backgrounds
cd ~/.backgrounds
wget -c [http://easylinux.info/uploads/change_background.py](http://easylinux.info/uploads/change_background.py)
chmod +x change_background.py

Same with the other command if you want to enable a different background on each reboot:

export EDITOR=gedit && crontab -e

The last one isn't a command. You are to enter this line into the editor (opened in the previous step), save the file and exit:

@reboot ~/.backgrounds/change_background.py

---

### Post by bionnaki on 2006-05-02
you probably just need to make the directory. right-click create folder and name as such.

---

### Post by steve.horsley on 2006-05-02
[QUOTE=Mark_in_Hollywood]From the Unofficial Ubuntu website, I "installed" the script to change the background wallpaper.

mkdir ~/.backgrounds
cd ~/.backgrounds
wget -c [http://easylinux.info/uploads/change_background.py](http://easylinux.info/uploads/change_background.py)
chmod +x change_background.py

[/QUOTE]

How much of those commands did you do? The first one creates the directory ~/.backgrounds. If you did that, the directory is there.

The tilde "~" means "my home folder". So "~/.backgrounds" probably means something like /home/mark/.backgrounds. Have a look there.

---

### Post by Mark_in_Hollywood on 2006-05-04
SUCCESS.

Thanks, all, I've got the wallpaper changing every time Ubuntu fires up. The images are pre-made wallpapers from the Hubble Space Telescope.

For those who like sci-fi, space, etc.

[http://hubblesite.org/](http://hubblesite.org/)

---

