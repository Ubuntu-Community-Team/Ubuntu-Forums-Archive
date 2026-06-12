---
title: "How do I open a bin file?"
date: 2006-11-25
forum: Absolute Beginner Talk
---

### Post by DougieFresh4U on 2006-11-25
Good morning taurus, could you please help me open a bin file? Currently it's /home.dougie/desktop  and it's file: WW2D-0.99.88RC1-lin.bin

---

### Post by taurus on 2006-11-25
Good morning to you too, DougieFresh4U.

It depends on what WW2D-0.99.88RC1-lin.bin is!  You can use bin2iso to convert it to ISO and then mount it with the mount command from a terminal...

```
bin2iso WW2D-0.99.88RC1-lin.bin
sudo mount -t iso9660 -o loop WW2D-0.99.88RC1-lin.iso
```
Otherwise, you can use k3b to burn it directly to your CD/DVD...

---

### Post by Aranel on 2006-11-25
Or if it's just a file that needs to be executed, you can open a terminal and do this:

```
cd Desktop
chmod a+x WW2D-0.99.88RC1-lin.bin
./WW2D-0.99.88RC1-lin.bin
```

The "cd" changes directory so that you're "at" your Desktop; the "chmod" changes the type of file it is, to make it executable; and the last command executes it.

---

### Post by asnd16 on 2007-01-12
ok I have a bin file but I am unable to get it open, II tried above exactly but I get the following error

./home/moses/Downloads/Picnic at Hanging Rock (1975) [DVDrip AVC AAC][liDEL]/Pans Labyrinth (2006) DVDSCR-G-TEAM (A UKB KVCD by Dev)/Pans Labyrinth (2006) DVDSCR-G-TEAM (A UKB KVCD by Dev).bin' 
bash: syntax error near unexpected token `('

---

### Post by taurus on 2007-01-12
Is that a movie file?  If it is, then you can play it directly without mounting it first...

Applications -> Accessories -> Terminal
```
gmplayer **filename.bin**
```

---

### Post by tvor on 2007-04-08
Hello Taurus! For me movie in > gmplayer works perfectly. I don't understand- it is impossible to know what .bin file actually is ( is it just and image as .iso)? And it there any way to play this movie directly with Totem movie player? 
Thank you:)

---

