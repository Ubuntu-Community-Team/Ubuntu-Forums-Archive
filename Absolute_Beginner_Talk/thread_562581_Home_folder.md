---
title: "Home folder"
date: 2007-09-28
forum: Absolute Beginner Talk
---

### Post by pchitti on 2007-09-28
OK so I managed to change the defualt program to open my home folder to VLC media. Im running Kubuntu Fiesty on a MT6840 gateway. Bought it about 3 weeks ago and I installed this right after. But back to the issue. my home folder opens in VLC, no longer shows folder,files, or anything other then videos. It scrolls through the files until it finds one it can play. any help on changing the default for it back with out being able to get to the file??
:confused:

---

### Post by Shazaam on 2007-09-28
nevermind, llamakc has a better solution.
Right-click your /home folder, choose Properties>Open With. Unless you have changed it numerous times the default open-with should be listed along with vlc.

---

### Post by pchitti on 2007-09-29
I cant get to the home folder. The only way I know how is through the kde bar on the bottom of the screen. The only options I r for the tool bar configure. I need to reset the home folder default program but dont know the command. Or if I there is a command to open under a different app.

---

### Post by llamakc on 2007-09-29
When you say your "home" directory do you mean /home or do you mean /home/USERNAME or /home/USERNAME/Desktop?

type alt-f2 and enter

nautilus --no-desktop /home

now right-click on your username's home folder and fix it.

My bad. I didn't pay attention to what you said about using Kubuntu.

Do this instead:

Open whatever run-dialog KDE has (or a terminal) and type:

konqueror /home

and right click on your user's /home/USERNAME folder and choose "open with"

---

### Post by pchitti on 2007-09-29
OK I now have the property menu pulled up with the open with screen. All I get is a tree of the programs on my comp. I dont know what the default program is for the home folder....

---

### Post by llamakc on 2007-09-29
On KDE it is /usr/bin/konqueror

---

### Post by pchitti on 2007-09-29
Perfect thank you so much.

---

