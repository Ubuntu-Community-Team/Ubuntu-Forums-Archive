---
title: "How do I go back to the Lucid theme on Maverick?"
date: 2010-10-01
forum: Art &amp; Design
---

### Post by nepenthe on 2010-10-01
I’d like to have the Lucid (10.04) theme back in Ubuntu Maverick (10.10). Any ideas how to do it?

Anybody else who doesn’t like flat buttons and the colour orange? ;>

---

### Post by JosephC on 2010-10-01
I like the Maverick design. I think it is sleeker. The lines are cleaner, I prefer flat buttons, like the orange color a lot, and much prefer the new color scheme of Radiance, which is a huge improvement. However, to each his own until somebody gets hurt.

I don't know if this will work, but we can try.

Firstly (and this is very important), open Appearance Preferences and  change your theme to anything but Ambiance or Radiance. You could go  Clearlooks or Dust. Of course, both ways are nice. 

I do not have Maverick, but I would now try to completely remove the 'light-themes' package with Synaptic, then try installing the original Lucid 'light-themes' package from Launchpad.

If you want to change yours back to the Lucid version manually, it should be easy. You just have to learn where everything is hidden in the File System, to see where themes are called from.

Now simply push Alt+F2 on your keyboard to open the Run Application window, and then run 'gksu nautilus' in order to open an administrator's file manager window that will allow you to freely modify the contents of the file system. You will have to enter your password to open the window. 

Or, if you prefer, install 'nautilus-gksu' (without quotes) from Synaptic, if you have not already, and restart. This will add "Open as Administrator" to your right-click context menu. This way, you can open any folder or file as administrator directly through the GUI from now on. 

If you chose the first option, navigate to File System in the new administrator Nautilus file manager. It should be under Places in the left panel. If it is not there for whatever reason, click back to the first breadcrumb. Then navigate to the 'usr' folder, and then to 'share'.

If you chose the second option, just click on Computer under Places in the main menu. Navigate to File System. Right-click on the 'usr' folder. Open as Administrator. Enter password. Navigate to 'share' in new administrator window. 

Once in the 'share' folder, navigate to themes. Behold: Ambiance and Radiance folders. The contents of these are everything in the universe proximately responsible for that specific arrangement of pixels you call themes. Delete them!

Or move them to be safe. Your call. 

Reboot.

Now you have to get the original Lucid themes. Here is the link:

[http://launchpadlibrarian.net/44360837/light-themes_0.1.6.5_all.deb](http://launchpadlibrarian.net/44360837/light-themes_0.1.6.5_all.deb)

Once downloaded, run it and install if possible, ignoring any possible message that a newer version is available in the repository. 

 If for whatever reason they will not install, right-click on the .deb and extract its contents. Somewhere in there you will find two folders very much like the ones you just deleted (or moved) in '/usr/share/themes'. Ordinarily, I would say that just moving them to that location would work, except that themes usually like to be installed properly.

So, open Appearance Preferences. Click the Theme tab. Drag and drop the Ambiance and Radiance folders from the extracted .deb in the Themes window in order to install them.

Now they are installed, for good or ill. I am not sure how these themes will look in Maverick, but they should work okay. Maybe. Hopefully. 

But there is still a small problem. Installing any theme via the Appearance Preferences' Themes tab only installs the theme(s) for the current user. This will have the effect of making every administrator window revert to an unthemed state. It is very ugly. Essentially, it copies the folders to your user directory under '.themes', which is a hidden file. You can find them by opening your Home Folder under Places. Then you click View in the menu and then check 'Show Hidden Files'. 

 However, after you install a theme via Appearance Preferences, it seems it will look in both locations ('/Home/*user*/.themes' and '/usr/share/themes'). Thus, you can cut the folders from '/Home/*user*/.themes' and paste them into '/usr/share/themes' and then reboot.

After this, the original Lucid Light Themes should be properly installed and selectable from the Appearance Preferences' Themes tab. 

Hope it works.

---

### Post by davidjnice on 2010-10-28
Hi.  I repackaged the Lucid (10.04) light-themese themes so that they can be installed on maverik (10.10).  They will install alongside the new light-themes and appear as lucid-ambiance & lucid-radiance.

I'll get round to making a deb for them eventually but for now, pick them up here...

[http://www.davidjnice.com/projects/lucid-themes.html](http://www.davidjnice.com/projects/lucid-themes.html)

---

### Post by graffiX on 2010-12-10
> **davidjnice said:**
> Hi.  I repackaged the Lucid (10.04) light-themese themes so that they can be installed on maverik (10.10).  They will install alongside the new light-themes and appear as lucid-ambiance & lucid-radiance.

I'll get round to making a deb for them eventually but for now, pick them up here...

[http://www.davidjnice.com/projects/lucid-themes.html](http://www.davidjnice.com/projects/lucid-themes.html)

Thank you so much for this David!  I was sad to see the theme change, but also annoyed that it was the "same" theme!  So a huge thank you for your de-ugly of Maverick!

Regards,

Dave

---

