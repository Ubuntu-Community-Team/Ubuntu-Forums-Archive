---
title: "Wine"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-07
I have installed wine following "http://ubuntuforums.org/showthread.php?t=149585" these instructions, but how do I install programs and can I start it like windows desktop. I want to install ms office so I could work there

---

### Post by louis_nichols on 2006-08-07
well... you install programs pretty much as you would in windows, except you fire executables using "wine *name.exe*". Then, you get all the windows with Next>Next>Finish stuff, just as you would in windows, depending on the installer. Wine will even place the shortcut on your gnome desktop, like it would appear in windows.

Now, with office... it might not be that easy. There is a package called crossover office, which can help you install ms office in Linux. But it isn't free, and I haven't heard of them going out of business, so I don't know if office can be installed under the simple wine.

I just use OpenOffice. It's better tha some say.

---

### Post by vaazu on 2006-08-07
Actually I have MS office cd can i use it?

---

### Post by AirRaven on 2006-08-07
> **vaazu said:**
> Actually I have MS office cd can i use it?

Of course you can!

Just pop it in and doubleclick whatever the setup.exe/install.exe file is on the CD. It'll open it in Wine automatically and install.

However, I reccomend you run "winecfg" first and click on the "Drives" tab. Click "autoconfigure"- it'll allow Wine to recognise your optical drives.

When you use Wine applications, you'll probably be put off by how ugly they are. The problem's easily solved- the latest version of Wine supports the .msstyles format used in Windows XP for theming. This means that you can either use your standard Windows XP style in Wine, or use a more Linux-centred style. I reccomend [this](http://www.deviantart.com/view/18591720/) style for Linux integration- a port of Clearlooks to Windows XP's MSstyles format. Integrates very nicely indeed if you're using the standard Ubuntu "Human" theme.

To use msstyles with Linux, copy the contents of the folder C:\Windows\Resources\Themes from your Windows installation (if you have one) to /home/yourusername/.wine/drive_c/windows/Resources/Themes. If you don't have XP, then you can use the theme I linked you to earlier by putting the "Clearlooks" folder in the archive in the /Themes folder. Then just run "winecfg" and go to the "Desktop Integration" tab. Choose the theme from the dropdown list provided, and click apply- it'll make running applications under Wine so much more bearable when you've got rid of that ghastly concrete-grey colour.

---

