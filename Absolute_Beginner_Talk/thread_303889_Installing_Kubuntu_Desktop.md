---
title: "Installing Kubuntu Desktop"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by jedimasterk on 2006-11-21
After I installed the Kubuntu desktop I get the Kubuntu logo when I boot Ubuntu. How do I get back the Ubuntu logo.

---

### Post by hearnden on 2006-11-21
See [http://help.ubuntu.com/community/USplashCustomizationHowto](http://help.ubuntu.com/community/USplashCustomizationHowto)

If the Ubuntu USplash logo is still around, then you can skip most of that guide up to:

```

sudo update-alternatives --config usplash-artwork.so

```

And switch away from anything with 'Kubuntu' in it and go for the one with 'default' in it, and then rebuild the initramfs as per the guide.

If Kubuntu has overwritten the default USplash logo, then you may need to do some googling to get a copy of the default one and follow the guide from the beginning.

---

