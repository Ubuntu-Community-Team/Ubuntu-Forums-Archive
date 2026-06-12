---
title: "[SOLVED] Configuring SAMBA with a gui and also restricting access to only shared fold"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by mister_lister on 2007-10-07
I have two questions regarding a windows\linux share workgroup using SAMBA. I have a windows network with win 98 se and linux (ubuntu 6.06 - fully updated).

The first question: Is there a GUI tool available for configuring samba that works with ubuntu 6.06?

The second question: Instead of only my specified share folder being seen, the whole linux  home\"user" files and directories are displayed on the win 98 se machine. I set up a share usinging the System>Administration>Shared Folders, it is available and marked as a share but the entire user directories are displayed and accessable. Is there a way to restrict access from other computers to just that shared folder?

---

### Post by ryanVickers on 2007-10-07
about #1 - just right clikc the folder and click "share this folder" or something, and then a little box will ask you "no sharing, samba (windows/smb), or nfs (unix)"

---

### Post by mister_lister on 2007-10-07
Question #1: (SOLVED) It's not really necessary to have a tool that I was looking for, the configuration is just a text file that I can open with nano, I was just looking for something GUI, but it is not really necessary.


Question #2: (SOLVED) The forementioned configuration file for samba is in /etc/samba/smb.conf . I discovered that my share was appended to the end of that file and it's path was my home/"user" directory rather than /home/"user"/My_Share. So I just edited the path to what I wanted it to be and now it is sharing only that "My_Share" folder. Seems like a bug because I explicitly indicated I wanted to share only that path when I set up the share. Strange. I double checked before editing and the System>Administration>Shared Folders dialog box showed the correct path but the config file didn't reflect that. Anyway it is solved.

---

