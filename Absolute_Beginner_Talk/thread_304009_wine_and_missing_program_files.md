---
title: "wine and missing program files"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by benner on 2006-11-21
i supposedly have wine installed on edgy and when i run winecfg from the terminal i can change various settings.  the windows application installed in a seemingly correct way.  in winecfg the program does not appear in the applications list but when i select 'add' it is there and i can add it to the list.  a wine shortcut to the program files never appears and i can't find the file in the computer anywhere (except when i open winecfg).  when i open winecfg again, the application that i just added a minute ago is no longer there.
i have edgy running on 5 machines and all of them are doing the same thing.  do i need to do something to set it up that i am missing?  in dapper, i had it running but i don't remember doing anything different.  perhaps i forgot.  can anyone help me out?

---

### Post by Jimmey on 2006-11-21
Wine's configuration files (as with most other applications'), are kept in hidden directories in your $HOME.

In Wine's case, they're in /home/username/.wine/. Hidden folders and files can be viewed, in Nautilus, by pressing CTRL + H in a Nautilus window.

In Wine's configuration directory, there's a folder called drive_c. In that folder, there's a folder called Program Files. Wine creates a virtual C drive in the configuration directory, to which all of your programs files are installed.

To find out where your programs have been installed (assuming you installed the by running the installation .exe with wine), try > ls /home/username/.wine/drive_c/P[tab] (replace "username" with your username, and press tab at the appropriate point :-P).

You should see at least one folder that will probably contain the files needed to run your Windows program. If you installed Reflex, for example, you should see a folder called Reflex.

If you do see the folder[s] that you're looking for, then the executable files for that program will be in there. All that's necessary now is to CD to that folder (try typing the first few characters of the folder's name, and pressing tab), to find the executable's name (once you've CDed in, try > ls *.exe), and to run the executable: > wine nameof.exe.

Hope I helped.

---

