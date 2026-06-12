---
title: "Wallpapoz"
date: 2006-05-01
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-05-01
Anyone else found that wallpapoz is just not worth the effort?
On my system it seems to just have a mind of its own.

First i found i had to get it going again after every new boot-up. 

then however, i found that i tried changing images on different desktops and it wouldn't

Now, i've just booted up and i havent had to get wallpapoz going but on the contrary it seems to be running already except with only one of the images i had set on all of the desktops.

For the extra resources it is sucking off my system to run it probably just isn't worth it, although i enjoyed being able to customize and identify each of the desktops initially.

phew....

--
sophtpaw

---

### Post by testube_babies on 2006-05-01
If this is really an important part of your computing experience, perhaps you should try out KDE.  It has the option for different wallpapers per workspace built-in.

---

### Post by Rinzwind on 2006-05-01
Regarding your 1st complaint: in the read/install text file it says you need to put the daemon  into your startup dir. 
> The daemon program name is daemon_wallpapoz.py. You need to add this program into Gnome start up programs list if you want every time you log into Gnome session, your Gnome desktop will have the ability to have different wallpapers for different workspaces.

---

### Post by sophtpaw on 2006-05-01
[QUOTE=testube_babies]If this is really an important part of your computing experience, perhaps you should try out KDE.  It has the option for different wallpapers per workspace built-in.[/QUOTE]

Yes, that's right. I will eventually swap over to kubuntu i reckon.

BUT, what is with the cat? some kind of stick-up?

--
sophtpaw

---

### Post by sophtpaw on 2006-05-01
[QUOTE=Rinzwind]Regarding your 1st complaint: in the read/install text file it says you need to put the daemon  into your startup dir.[/QUOTE]

Hmmm...too late for that now. I've already uninstalled it. But out of interest and for future reference where would i find the Gnome startup dir?

--
sophtpaw

---

### Post by Rinzwind on 2006-05-01
After you create a configuration file you can set the daemon to run every time you boot Ubuntu by selecting from the menu: 

>Systems
>Preferences
>Sessions 

Then the tab for 'Startup Programs', choose 'Add' and enter:
daemon_wallpapoz

(BTW this works for any daemon or program that has no output ;) )

I have 10 wallpapers for each of my 3 workspaces.

It's a bit slow but does work :)

---

### Post by sophtpaw on 2006-05-01
[QUOTE=Rinzwind]After you create a configuration file you can set the daemon to run every time you boot Ubuntu by selecting from the menu: 

>Systems
>Preferences
>Sessions 

Then the tab for 'Startup Programs', choose 'Add' and enter:
daemon_wallpapoz

(BTW this works for any daemon or program that has no output ;) )

I have 10 wallpapers for each of my 3 workspaces.

It's a bit slow but does work :)[/QUOTE]
Thank you Rinzwind,

That is useful knowledge,

--
sophtpaw

---

### Post by Rinzwind on 2006-05-01
No problem.
Some more useless info: did you know the creator of that is on these forums too? :)

Oh and it still works as intended overhere ;) Give it another shot :D

---

### Post by sophtpaw on 2006-05-01
[QUOTE=Rinzwind]No problem.
Some more useless info: did you know the creator of that is on these forums too? :)

Oh and it still works as intended overhere ;) Give it another shot :D[/QUOTE]

Well, ok, you twisted my arm, and so i've given it another chance:rolleyes: 

However, unfortunately, it just isn't working here. I've gone and added the line in System/preference/sessions. I added daemon_wallpapoz in the startup like  you suggested.

for good measure i rebooted and tried to reset the wallpaper but they won't play game. I'm not saving any new or other backgrounds or wallpapers and it is the same mess everytime. 
I click 'save' and restart daemon or whatever it is but nada :confused: 

What's wrong with gnome that it hasn't got it in-built like kde does to be able to configure however many desktops one has as one would like? argh...

--
sophtpaw

---

### Post by halfvolle melk on 2006-05-01
Your topic reminded me that I wanted to try this so I did erlier today.

Do it by the numbers. The 'readme' and 'install' state (<bla> is me):
> Extract wallpapoz package
$ tar -jxvf wallpapoz-0.3.tar.bz2
Go to wallpapoz directory
$ cd wallpapoz-0.3
<ignore the bit about root>
run "wallpapoz.py"
<select what wp you want for each desktop instance thingy>
<do as suggested:
[i]>Systems
>Preferences
>Sessions

Then the tab for 'Startup Programs', choose 'Add' and enter:[/i]
in my case very inappropriately:
/home/jz/Desktop/wallpapoz-0.3/src/daemon_wallpapoz.py >

Now, don't reboot. Just log out and in again. It's slow but it works.
Good luck.

edit: first remove ~/.wallpapoz before doing the above.

---

### Post by sophtpaw on 2006-05-01
[QUOTE=halfvolle melk]Your topic reminded me that I wanted to try this so I did erlier today.

Do it by the numbers. The 'readme' and 'install' state (<bla> is me):


Now, don't reboot. Just log out and in again. It's slow but it works.
Good luck.

edit: first remove ~/.wallpapoz before doing the above.[/QUOTE]

It won't even let me change wallpaper. I change but after i save and restart daemon it is as it was before. I can't remove or change wallpapers

I'm sorry but this program sux. ](*,)  Sorry, Akbar.:D 

--
sophtpaw

---

### Post by halfvolle melk on 2006-05-01
I see you left out the essential bit in your quote. Did you try it like that?
Check the screeny, does that not work for you?

---

### Post by sophtpaw on 2006-05-01
[QUOTE=halfvolle melk]I see you left out the essential bit in your quote. Did you try it like that?
Check the screeny, does that not work for you?[/QUOTE]
yes

---

