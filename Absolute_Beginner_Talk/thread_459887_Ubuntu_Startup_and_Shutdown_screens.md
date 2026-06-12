---
title: "Ubuntu Startup and Shutdown screens"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by kevanf on 2007-05-31
I wish to change the Ubuntu Startup/Shutdown screens. how can this be done.

---

### Post by carloslosgrande on 2007-05-31
System>preferences>splash screen will let you change the startup screen
System>admin>login window for login.
I don't know about shutdown, unless you want to try the 'satanic edition' which sets up new screens for both startup and shutdown.

---

### Post by kevanf on 2007-05-31
Hi Thanks for the reply, I do not have a reference "Splash Screen" on my dropdown menu

---

### Post by ruscoe on 2007-05-31
Ubuntu uses usplash for boot screens. There are a few you can download from gnome-look,org that have installation instructions.

Here's one:
[http://gnome-look.org/content/show.php/Peace+Edgy+Usplash?content=47351](http://gnome-look.org/content/show.php/Peace+Edgy+Usplash?content=47351)

---

### Post by kevanf on 2007-05-31
Thankyou, Works fine. Do you know how to create a new one. I have a image I would like to use.

---

### Post by parker13 on 2007-06-05
> **kevanf said:**
> Thankyou, Works fine. Do you know how to create a new one. I have a image I would like to use.

There's some official documentation, but it isn't very good:

[https://help.ubuntu.com/community/USplashCustomizationHowto](https://help.ubuntu.com/community/USplashCustomizationHowto)


Here's a very quick tutorial on how I do it. It's not exact, but should get you started:

Note that these instructions only apply to Edgy and later - Dapper uses an older version of usplash with less colours.

There are three main parts to changing the usplash theme:

1) Artwork. You need to convert your image into a 256 colour .png format. I do this with The GIMP.

- Load your image in to The GIMP.
- Make sure it only has a single layer (Image->Flatten Image).
- Resize it to 1024x768.
- To reduce the number of colours, select "Image->Mode->Indexed".
- Select "Generate optimum palette" and set the number of colours to 256. Experiment with the dithering settings to see what works best for your image. This is important because some images look much better
with certain dithering methods.
- Save the image as .png.

- Repeat for sizes 800x600 and 1365x768.

2) Source code. You need to download the source code. I'd base it on the xubuntu package:

apt get source xubuntu-artwork-usplash

- Try compiling the source. You will need to install some packages to do this:

sudo apt-get update
sudo apt-get install dpkg-dev build-essential fakeroot

# Get the source and dependencies
sudo apt-get source xubuntu-artwork-usplash
sudo apt-get build-dep xubuntu-artwork-usplash

# Change the files to be owned by your user (replace garry with your username)
cd xubuntu-artwork-0.11
sudo chown -R garry:garry *

# Compile the software
make

# This creates the .so file:
usplash/usplash-theme-xubuntu.so


- Once you have it compiled, replace the images with the ones you have made and recompile.


3) Installation. The compilation process generates a .so file. Copy it to /usr/lib/usplash. To install it, run (assuming it is called "test-usplash.so"):

sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/test -usplash.so 10

sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u

- Test with sudo usplash -c


Sorry that I don't have the exact process, but this should hopefully help. Any questions, let me know.

---

### Post by kevanf on 2007-06-07
Hi, Thanks for your reply. I will try you instructions and let you know how I get on.

---

