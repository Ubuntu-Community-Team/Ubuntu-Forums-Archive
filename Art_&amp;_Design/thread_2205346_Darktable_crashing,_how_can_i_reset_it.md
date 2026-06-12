---
title: "Darktable crashing, how can i reset it?"
date: 2014-02-13
forum: Art &amp; Design
---

### Post by Coder88 on 2014-02-13
I have the current version of ArtistX installed on my PC (AMD64, 6 core, 16GB RAM). I want to reset **Darktable**, reset any settings I changed that might be causing it to crash immediately upon trying to import an image. It was working great.  I tried uninstalling Darktable then reinstalling, but still it retains settings and prior lists of folders of imaged edited. I looked in my home folder for .darktable hoping there would be such a configuration folder storing settings but there is no such folder/file of retained settings. Where the frack does Darktable store user settings, so I can delete that file wherever it is?

Right now Darktable is unusable, I wish someone could help me solve this riddle of getting it back to the way it was, working.

---

### Post by Portaro on 2014-03-05
You can use purge remove package context that method is the best effective to delete preference settings of come package on default package path, 

apt-get --purge remove <package>
apt-get clean

the later will clean the /var

To dissipate if the problem is on package or some launch fault on graphic render you can try also run darktable with 
LIBGL_ALWAYS_SOFTWARE=1 darktable ;

I need use the above command for some programs like blender because I have a precarious graphic performance with my unmaintained ATI Graphic card.
(This is a method to view if your problem is a result of malconfigure of program, or your problem is the graphic card performance with image renderize).
Any problem comment to us.

---

