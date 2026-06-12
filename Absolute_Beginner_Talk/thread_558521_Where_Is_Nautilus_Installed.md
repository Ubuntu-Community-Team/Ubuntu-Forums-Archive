---
title: "Where Is Nautilus Installed?"
date: 2007-09-24
forum: Absolute Beginner Talk
---

### Post by Sonic Reducer on 2007-09-24
i've been using EasyTAG to organize my mp3 collection, and i was trying to open a directory in nautilus through the right-click menu, but i have to select the program to do it with. i'd want to use nautilus right?

---

### Post by alienexplorers on 2007-09-24
Nautilus is just a file browser like windows explorer is in windows.  I have no idea what you want to use it for.  If you could explain further maybe we could help you out.

---

### Post by rabbit83 on 2007-09-24
It's ```
/usr/bin/nautilus
```

---

### Post by Sonic Reducer on 2007-09-24
i mean i want to select "Browse Directory With..." from the right-click menu and open up the folder in nautilus

---

### Post by Sonic Reducer on 2007-09-24
> **rabbit83 said:**
> It's ```
/usr/bin/nautilus
```

Perfect! thank you Rabbit

now is there a way to make it do that by default? i have to navigate to **/usr/bin/nautilus** every time i want to open a directory

---

### Post by dptxp on 2007-09-24
Click on system>preferences>MainMenu. Add there.

---

### Post by julian67 on 2007-09-24
> **Sonic Reducer said:**
> i've been using EasyTAG to organize my mp3 collection, and i was trying to open a directory in nautilus through the right-click menu, but i have to select the program to do it with. i'd want to use nautilus right?

Yes use nautilus. Right click>browse directory with>nautilus

or thunar for Xfce, konqueror for Kubuntu etc

Once you've added nautilus 1st time then it will appear in the drop down menu in future. 

I use Xubuntu and thunar and this feature of easytag works fine

---

### Post by Sonic Reducer on 2007-09-24
> **julian67 said:**
> Yes use nautilus. Right click>browse directory with>nautilus

or thunar for Xfce, konqueror for Kubuntu etc

Once you've added nautilus 1st time then it will appear in the drop down menu in future. 

I use Xubuntu and thunar and this feature of easytag works fine

it still asks me what i want to use to open the directory. is this going to be one of the things i just have to get used to not working?

---

### Post by julian67 on 2007-09-24
> **Sonic Reducer said:**
> it still asks me what i want to use to open the directory. is this going to be one of the things i just have to get used to not working?
 
On my system it asks me what I want to use and the different options (i.e. applications I previously specified) are in a drop down sub menu. This seems fine to me.  I installed from  deb. maybe it's worth looking at the source to check if you can build it with a pre-determined default file manager. And there are other tagging applications you could try. Kid3 is particularly good but is rather simpler than easytag and is a KDE app and also not cross platform like easytag (which is available for Windows too).  Picard is also worth investigating. Various media players also have mass tagging functionality, probably a search on google and with Synaptic will give you a few different ones to try, one of which might be what you're looking for.

---

