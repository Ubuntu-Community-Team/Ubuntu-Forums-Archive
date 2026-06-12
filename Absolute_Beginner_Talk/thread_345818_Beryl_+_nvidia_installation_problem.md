---
title: "Beryl + nvidia installation problem"
date: 2007-01-24
forum: Absolute Beginner Talk
---

### Post by Nightmist on 2007-01-24
Hello,

I ran into a problem when trying to install the nvidia beta drivers, as was suggested by this HOWTO.
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_nVidia)

> First, select one apt repository from the sections below. One way to do so is by running: 
sudo echo -e "\n## nVidia driver repository\n*repository*" >> /etc/apt/sources.list

where repository (in italics) is one of the strings listed in the gray boxes (beginning with deb) below. The current supported architectures are i386 and amd64. 
[edit]
Repository for stable drivers [recommended] 
deb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable

So, as far as I can tell, that should be like this:

> sudo echo -e "\n## nVidia driver repository\ndeb [http://nvidia.limitless.lupine.me.uk/ubuntu](http://nvidia.limitless.lupine.me.uk/ubuntu) edgy stable" >> /etc/apt/sources.list

Or did I misunderstand something? It doesn't make sense to me anyway, so I don't know if I got it right. Because I get the following error:

bash: /etc/apt/sources.list: Permission denied

---

### Post by Nightmist on 2007-01-24
I was just thinking... Even if the command isn't correct, should I still get the...

> bash: /etc/apt/sources.list: Permission denied

...error message?

---

### Post by Nightmist on 2007-01-25
Sorry to bump this, but I am still confused by what I am doing wrong.
:confused:

---

### Post by Nik_Doof on 2007-01-25
Just edit the sources file

```
sudo nano -w /etc/apt/sources.list
```

and paste in the lines:

```

## nVidia driver repository
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable

```

---

### Post by geokok1981 on 2007-01-25
You might want to try the script they provide at the top of their guide. It does everything automatically and saves you the trouble.

---

