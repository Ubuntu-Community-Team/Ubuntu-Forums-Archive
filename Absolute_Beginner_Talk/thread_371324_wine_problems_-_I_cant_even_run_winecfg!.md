---
title: "wine problems - I cant even run winecfg!"
date: 2007-02-26
forum: Absolute Beginner Talk
---

### Post by Tahir on 2007-02-26
hello all,

I am having problems with WINE and I dont know how to go about solving the problem. I have gone through loads of pages and learned loads of things (about linux and the command line) but I will not be able to sort out this problem without the help of someone on this forum.

Here is what I did:

installed wine, then ies4linux, then followed the following page to make it work:

[http://appdb.winehq.org/appview.php?iVersionId=3214](http://appdb.winehq.org/appview.php?iVersionId=3214)

There was nothing in the Library box so I added the following:

msxml3 (native)
usp10 (native)
riched20 (native)
shdocvw (native)
shlwapi (native)
mshtml (native)
urlmon (native)
wininet (native)

I made them native only so would that be a problem?

after that it of course the office 2003 installation did not work and strangely even winecfg did not work.  So here is the output:

> tahir@tahirs:~/Desktop$ winecfg
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\comdlg32.dll") not found
err:module:import_dll Library comdlg32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\shell32.dll") not found
err:module:import_dll Library shell32.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:import_dll Library shlwapi.dll (which is needed by L"c:\\windows\\system32\\winecfg.exe") not found
err:module:LdrInitializeThunk Main exe initialization for L"c:\\windows\\system32\\winecfg.exe" failed, status c0000135

winecfg ran properly before and it did not say these things.  Also I dont have a file ~/.wine/config. I know I can create one but I dont have any template and also would this even make a different considering that the global config file I am running is so messed up?  I have also tried uninstalling and reinstalling wine but with no luck.  Which file does wine write to when I configure winecfg and how would I edit that using a simple text editor? Is there any way I can restore the original configuration file in its place? Please help.  I really appreciate it.  Thanks everyone.

P.S I was trying to get MS Office 2003 to work with Wine and if you have got it to work please tell me.  If I get it to work then I will write up a how to on my website.

---

### Post by Patrick K on 2007-02-26
You might try running Synaptic and do a search for wine. Right click on it and select "mark for complete removal" then apply. Try reinstalling it again.  I don't know that this will get rid of your problems but it shouldn't make things worse. 

I think, but don't know this, that without using the complete removal option (or purge at the terminal), the installation files are reused and the config files remain in place and are reused. Complete removal should get rid of these files and give you a fresh download and install of wine. Anyway, that's what I'd try.

---

### Post by viper on 2007-02-26
Also after you perform a "complete removal" try this in the terminal.

sudo apt-get autoclean

Check this thread for a more detailed description.

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by Tahir on 2007-02-26
None of that worked unfortunately.  Would you be able to tell me where the configuration files are kept?

I have no idea where I would look.  In windows it would be

/c/Documents\ and\ Settings/name_of_person/Application\ Data/

for the user's configuration stuff but with Linux I am sure that they would have other places to put their stuff so what do I do???

---

### Post by Maestro23 on 2007-02-26
> **Tahir said:**
> None of that worked unfortunately.  Would you be able to tell me where the configuration files are kept?

I have no idea where I would look.  In windows it would be

/c/Documents\ and\ Settings/name_of_person/Application\ Data/

for the user's configuration stuff but with Linux I am sure that they would have other places to put their stuff so what do I do???

I don't use wine, but a user's config files are kept in his home directory. Try:

Open terminal and go to your home directory.

> cd /home/username

ls -a (shows hidden directories)


Will start with a "."
Hope that helps.

---

### Post by Tahir on 2007-02-27
Maestro23,

I deleted that folder and I reinstalled wine and although I have not tried installing office 2003 yet, winecfg works so that is a step in the right direction.  What it I was running wine in root that is "sudo su" my password then "wine"? would there be a folder /home/su/.wine/ or is that not how linux works?

Thanks again to all you guys. what I need now is to experiment a little and see how things go.

Cheers,
Tahir

---

