---
title: "[SOLVED] Redirecting a directory?"
date: 2007-11-27
forum: Absolute Beginner Talk
---

### Post by mivo on 2007-11-27
Morning guys. I have a 10 GB / partition and a separate (240 GB) /home partition. This usually works well, but now I want to install Enemy Territory, which wants to install to /usr/local/games. It's rather large and I would prefer the data to be kept on my /home partition. I know this can be done (redirecting/linking the directory), but I'm unusure how to do it exactly.

Thanks for any pointers!

---

### Post by mattmole on 2007-11-27
Hi,

Create the directory in your home directory and then at the terminal try the following:

sudo ln -s /usr/local/games/enemy_territory /home/USER/PATH/TO/DIRECTORY

You will probably need the sudo command to run the command as root due to the permissions of /usr/local/*

mattmole :-)

---

### Post by PointyWombat on 2007-11-27
Greetings, 

cd /usr/local/games
sudo ln -s ~<YourLoginID>/enemy-territory

This will create a link under /usr/local/games called enemy-territory which will actually live in your home dir.

HTH,

---

### Post by mivo on 2007-11-27
Thanks! Much appreciated! :)

---

