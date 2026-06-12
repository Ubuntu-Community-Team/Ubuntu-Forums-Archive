---
title: "Gkrellm"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-07-09
Hi, I just installed Gkrellm and i went to this website [www.muhri.net](www.muhri.net) and downloaded a theme for Gkrellm.

Does anyone have any experience with Gkrellm or have a command i can use to apply this theme to my Gkrellm device?

Thanx!

---

### Post by dksdk on 2006-07-09
> **IrishGangsta said:**
> Hi, I just installed Gkrellm and i went to this website [www.muhri.net](www.muhri.net) and downloaded a theme for Gkrellm.

Does anyone have any experience with Gkrellm or have a command i can use to apply this theme to my Gkrellm device?

Thanx!
hi extract the theme i,e right click on it and click on extract here.
this will create a directory with the theme name.
then copy this directory to and paste it to /.gkrellm2/themes
to make the hidden files visible in nautilus press ctrl+h when you are in nautilus. this will show the .gkrellm2 directory and select themes from there.
to apply your theme  right click on the top border of running gkrellm
select themes and up and down buttons.

---

### Post by IrishGangsta on 2006-07-09
at what point do i right click on it?
Right now its saved to my desktop
When i open it i get a bunch of more files.
Where can i find the directory path at?

---

### Post by dksdk on 2006-07-09
hi can you tell me what is the file type you have downloaded, is it a tar.gz.
what is the file extension?

---

### Post by DR_K13 on 2006-07-09
You can also
```

apt-get install gkrellm
```


then add themes later ///

---

### Post by IrishGangsta on 2006-07-09
Ok, i am trying to find this out now.
All i know is the i went to [www.muhri.net](www.muhri.net)
I clicked on Gkrellm and on the bottom where it says Skin Name type: BlueMask
That is what i downloaded.
The File download is BlueMask-gkrellm.tar.gz
I opened with archive manager and extracted to desktop
Which is /home/mike/desktop


All i want to do is apply this downloaded theme to the gkrellm.

Thank you

---

### Post by dksdk on 2006-07-09
hi in that case you will have a folder called BlueMask in your /home/mike/desktop. copy this folder.
now go to your /home
press ctrl+h. scroll down to .gkrellm2 folder open it, will have a themes folder inside. open themes folder.
Now paste your BlueMask folder here.
Now you will have to restart gkrellm.
after restart right click on the top border of gkrellm and select themes.

---

### Post by IrishGangsta on 2006-07-09
Hey dksdk 
your awesome!

it works 
thanx

---

### Post by beatyou on 2006-07-11
Thanks this is exactly what I did, except through terminal.

---

