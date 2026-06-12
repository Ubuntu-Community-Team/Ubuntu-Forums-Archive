---
title: "How to Remove Ubuntu Font Rendering Patch"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by nb123 on 2007-09-16
Hi, I recently found this thread: ---

[http://ubuntuforums.org/showthread.php?t=515947](http://ubuntuforums.org/showthread.php?t=515947)

which had a link to this thread: ---

[http://tux.fau.edu/index.php/topic,93.0.html](http://tux.fau.edu/index.php/topic,93.0.html)

I used the "cd Desktop; chmod +x font_patch.sh; sudo bash font_patch.sh" command along with the font_patch.sh and installed it, but unfortunately I don't like the vertical anti-aliasing... Could someone please explain to me how to remove it?

---

### Post by nb123 on 2007-09-16
Just to make it clearer, I think this is what has been done: ---


#! /bin/bash
## Ubuntu Font Improver Patch
## by emet of FAU LUG ([http://tux.fau.edu](http://tux.fau.edu))

## Add special repository to apt sources list
echo "################################" >> /etc/apt/sources.list
echo "# Ubuntu Font Improvement Patch" >> /etc/apt/sources.list
echo "deb [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts" >> /etc/apt/sources.list
echo "deb-src [http://www.telemail.fi/mlind/ubuntu](http://www.telemail.fi/mlind/ubuntu) feisty fonts" >> /etc/apt/sources.list
echo "################################" >> /etc/apt/sources.list

## Get the GPG key for the repository
wget [http://www.telemail.fi/mlind/ubuntu/937215FF.gpg](http://www.telemail.fi/mlind/ubuntu/937215FF.gpg) -O- | sudo apt-key add -

## Update the APT database
apt-get update

## Install the needed packages
apt-get -y install libfreetype6 libcairo2 libxft2

## Now add Red Hat Liberation Fonts

## Download the fonts from Red Hat
wget [https://www.redhat.com/f/fonts/liberation-fonts-ttf-3.tar.gz](https://www.redhat.com/f/fonts/liberation-fonts-ttf-3.tar.gz)

## Extract the package
tar -xvf liberation-fonts-ttf-3.tar.gz

## Copy the fonts to the proper directory
cp -r liberation-fonts-0.2 /usr/share/fonts/truetype/

## Delete temporary files
rm -r liberation-fonts-0.2/ liberation-fonts-ttf-3.tar.gz

## Rebuilt the font cache
fc-cache

## Display confirmation
clear
echo "Ubuntu font improvement successfully installed!"
echo "Font rendering improved with subpixel and vertical anti-aliasing."
echo "Also installed new Red Hat \"Liberation\" font set. Very sexy fonts!"
echo "You must either restart your computer or restart the X Display to see the changes."
echo "Visit [http://tux.fau.edu/](http://tux.fau.edu/) for more tips and cool stuff."


how do I undo this?

---

### Post by taisao on 2007-09-16
try

```
sudo apt-get remove libfreetype6 libcairo2 libxft2
```

---

