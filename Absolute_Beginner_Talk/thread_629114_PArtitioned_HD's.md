---
title: "PArtitioned HD's"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by Unity_crew on 2007-12-02
So im using windows with severe thoughts about switching to Kubutu 7.10 and i have my HD with a 10gb partition of media files my question is this: will this partition work to open my media files when i switch to kubuntu???

Thanks a lot

---

### Post by overdrank on 2007-12-02
> **Unity_crew said:**
> So im using windows with severe thoughts about switching to Kubutu 7.10 and i have my HD with a 10gb partition of media files my question is this: will this partition work to open my media files when i switch to kubuntu???

Thanks a lot

Hi and welcome, If I understand you correctly, yes you will be able to access that partition with Kubuntu. You may need some tools to access it if it is NTFS. [http://swik.net/ntfs-3g-ubuntu-feisty](http://swik.net/ntfs-3g-ubuntu-feisty)

---

### Post by logos34 on 2007-12-02
linux reads ntfs natively, so it will detect it and add it to fstab.  Gutsy comes with ntfs-3g by default, so you will even be able to save (write) other media files to it.  You need the gui though. After you get ubuntu up and running, just open a terminal and do:

sudo apt-get install ntfs-config

sudo ntfs-config

>enable write support internal drives


more on [dual booting here]("http://www.psychocats.net/ubuntu/index.php")

---

