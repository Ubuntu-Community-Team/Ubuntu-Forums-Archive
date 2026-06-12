---
title: "Help a newbie with a couple of issues"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by jgf621 on 2007-01-04
My inexperience is in my way.  I want to do the following and continue to fail:

1.  Download Adobe Reade and install.
2.  Associate XMMS with mp3 files.
3. Add mp3 support to Movie Player

I've learned a little in the last week but keep stumbling here.

Thanks.](*,)

---

### Post by benuski on 2007-01-04
To change mp3 default playback to XMMS, right click on an mp3, hit properties, and then go to the open with tab and choose whatever program you like.
And as long as you have the proper codecs installed, found on the restricted formats wiki page, the movie player should be able to play mp3 files, as far as I know.

---

### Post by jgf621 on 2007-01-04
Thanks!  One more bites the dust.:-D

---

### Post by Izobalax on 2007-01-04
> **jgf621 said:**
> 
1.  Download Adobe Reade and install.

The only way I know of doing this is via [Automatix](http://www.getautomatix.com/).

HTH. 

:)

/izo

---

### Post by jgf621 on 2007-01-04
Thanks for tip.  I installed Automatix but can't locate Adobe Reader.  What have I missed?:-k

---

### Post by jem7v on 2007-01-04
For Acrobat (which is what I assume you mean by Adobe Reader) just install the **acroread** package from Synaptic.

---

### Post by DJ_Peng on 2007-01-04
Check your Applications > Graphics for a program called Document Viewer. If you have it it will open the Evince Document Viewer, which handles PDF files. I just used it for a PDF file I found online today, and I'm guessing it may even bypass the recent vulnerability found in Adobe's reader but don't hold me to that.

---

### Post by jgf621 on 2007-01-04
Tow answers.

How do I run Synaptic?
I have no Document Viewer listed.:-|

---

### Post by raul_ on 2007-01-04
I think you should take a look at [http://www.psychocats.net/ubuntu/index]("http://www.psychocats.net/ubuntu/index")

and
[http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy")

---

### Post by jgf621 on 2007-01-04
Thanks for the help.  I figured out a little but Acroread is not found anywhere.  Possible it's not available for Edgy yet?

I updated and looked at everything available but no abode reader.

---

### Post by raul_ on 2007-01-04
I have Adobe reader..i don't know what the package is though...i think i got it with automatix

---

### Post by riven0 on 2007-01-04
Perhaps you don't have all your sources enabled. Can you post the output of this?:

> cat /etc/apt/sources.list

---

### Post by Duck2006 on 2007-01-04
Did you look in add/remove programs

---

### Post by DJ_Peng on 2007-01-04
Do a search for Evince. That's the postscript/pdf reader that you need. I just double checked it in Synaptic, and it's in there.

---

### Post by raul_ on 2007-01-04
xpdf also reads pdf documents, but i thought he wanted adobe reader

---

### Post by jgf621 on 2007-01-05
I found this message regarding ACROBAT.

" Adobe Reader
The use, modification and distribution of Adobe Reader is restricted by copyright or by legal terms in some countries.
Adobe Reader cannot be installed on your computer type (amd64). Either the application requires special hardware features or the vendor decided to not support your computer type.

Is this the final answer or is there something to be done here?:(

---

### Post by jvc26 on 2007-01-05
I'm running AMD64 and I dont have adobe reader I just use Evince document viewer (comes with Ubuntu to my knowledge) and reads .pdfs just fine - is there any reason why you want acrobat in particular? If you don't have evince I'm sure you can get it via synaptic.
Il

---

### Post by jimbo2150 on 2007-01-05
Adobe Acrobat is available for edgy. Acrobat version 7, not 8 yet.

Open Synaptic (you will need your administrator password)
System -> Administration -> Synaptic Package Manager

Search for 'acroread' OR 'adobe' OR 'acrobat'. All of those seem to work.

Find the the 'acroread' package and mark it for install. It will automatically mark the other required packages including the plugins for internet browsers.

Install it.

To get MP3 support in media player (although I recommend using Banshee or Amorok for mp3s), choose 'Multimedia Codecs' (under Multimedia tab) in Automatix should work.

---

### Post by mhenriday on 2007-01-05
**Jgf621**, an **Adobe Acrobat Reader** can be found on **Automatix 2** ; just look under **Office**. And **acroreader** is found on your **Synaptic Package Manager**. In addition, if you don't absolutely require **Adobe**'s products, there is a plethora of **pdf** readers from which to choose on **Ubuntu 6.10**, and which all seem to work very well indeed. But not having a 64 bit machine myself, I don't know if they function with such a device. **OpenOffice.org**, which permits one to both read and write **pdf** files, is available on **Ubuntu** and can be highly recommended....

Henri

---

### Post by jgf621 on 2007-01-05
Searching in Synaptic for Adobe, acroread, etc. returns nothing. Have I missed a step?  I'll look at other pdf converters.

In the end, I'm looking to use Adobe inside Mozilla 2.0.  I'm not sure that plug-in is even ready yet.

The message saying it was not available for an AMD 64 came from Install and Remove Application.

Thanks.

---

### Post by raul_ on 2007-01-05
are u using the 64bit ubuntu? Install it with Automatix2
[www.getautomatix.com]("www.getautomatix.com")

---

### Post by jgf621 on 2007-01-05
Thanks to all for advice.  Evince works fine.  I think Adobe does not, for whatever reason, e.g. AMD 64 or in combo with EDGY and AMD 64.

---

### Post by jgf621 on 2007-01-05
For Riven0:

here's what you asked to see.

jgf@jgf-desktop:~$ cat /etc/apt/sources.list
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb [http://www.albertomilone.com/drivers/edgy/latest/64bit](http://www.albertomilone.com/drivers/edgy/latest/64bit) binary/


## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse universe

---

### Post by ramjet_1953 on 2007-01-06
Go to System>Administration>Synaptic Package Manager

It will then ask for your admin password.
Enter it and when Synaptic opens, click on Settings>Repositories

Make sure that there is an x in all of the boxes.
Also take the opportunity to select your closest server in the drop-down list.

Click on Reload. This will load all of the extra repository info.

Click on search and type in acroread.

It should find it and then you just right click on it and click on mark for installation.

Click on apply and it should be installed.

Regards,
Roger 8)

---

### Post by jgf621 on 2007-01-06
ALL of the boxes?  Why add German support and a chess game?  There are a lot of boxes.

---

### Post by DJ_Peng on 2007-01-06
He's just saying to check the boxes to make all the Repositories available, not to get everything in them. I have all the repository boxes checked and the German help and chess game never came across my notice. I'm just saying that being able to access the repositories get you everything you don't need. Once you can get into the repositories you'll be able to as well, and you can just ignore what you don't. That's what I do.

---

### Post by jgf621 on 2007-01-06
I had already done that and I did it again.  Neither  Acrobat nor Acroread nor Acroreader are found via search.

---

### Post by dannystaple on 2007-01-06
jgf621 - to find the packages (forgetting automatix for now), you need to tell the ubuntu package manager to pick up packages from the restricted repositories. 

Go to System->Administration->Software sources, and in the window that appears (after typing your password) , enable Community Supported Software (universe), Software Restricted By Copyright... (multiverse) and also Proprietary Drivers for devices (restricted). Close the window.

Open up synaptic with System->Administration->Synaptic, it will probably inform you that you need to reload, allow it to do so, then search for acroread and you should find it.

Done.

---

### Post by jgf621 on 2007-01-06
Did that, same result.  I should have mentioned that seaeching on Adobe via Synaptic gives me a few names like  "CMaps for Adobe-CNS1"  but no PDF.

---

### Post by mhenriday on 2007-01-07
**Jgf621**, I find it extremely difficult to understand why a search in **Synaptic** for «acroread» fails on your computer, in the event you have,as you say, followed **dannystaple**'s instructions above. But be that as it may, if you open **Synaptic**, click **All** in the left-hand window, and then scroll down in the one to the right, you should shortly come to the following three entries :
[INDENT]acroread 7.0.8-0.0.ubuntu2
acroread-escript 7.0.8-0.0.ubuntu2
acroread-plugins 7.0.8-0.0.ubuntu2[/INDENT]

Just check the little box to the write and click the «apply» checkmark, and the programmes will be installed on your computer....

Henri

---

### Post by jimrz on 2007-01-07
> **jgf621 said:**
> Thanks for the help.  I figured out a little but Acroread is not found anywhere.  Possible it's not available for Edgy yet?

I updated and looked at everything available but no abode reader.

sounds like you need to enable "multiverse" repo 

in synaptic  go to settings > repositories, check the box for multiverse (probably want to check universe, as well), close the settings window, hit the refresh button and it should be there for you to select / install

---

### Post by tchoklat on 2007-01-07
try here:

** How to install PDF Reader (Adobe Reader) with Plug-in for Mozilla Firefox **

 [LIST]
[*]Read [#General Notes]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#General_Notes")
[*]Read [#How to add extra repositories]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories")[/LIST] sudo apt-get install acroread mozilla-acroread acroread-plugins
[LIST]
[*]Applications -> Office -> Adobe Reader
[*]Restart Mozilla Firefox[/LIST] **Note:** Adobe Reader 7.0 will not run if SCIM is running. You are running SCIM if you have installed another language to Ubuntu via System -> Administration -> Language Support. To circumvent, do the following 
 gksudo gedit /usr/bin/acroread
Change: 
 #!/bin/sh
#

to: 
 #!/bin/sh
#
GTK_IM_MODULE=xim
Save the file.  Now Adobe Reader 7.0 should work. 
See also: 
 [LIST]
[*][#How to associate Adobe Reader with files in Nautilus]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_associate_Adobe_Reader_with_files_in_Nautilus")
[*][#How to print from Adobe Reader]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_print_from_Adobe_Reader")
[*][#How to pull apart and combine pdf files]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_pull_apart_and_combine_pdf_files")[/LIST] [[edit]("http://ubuntuguide.org/index.php?title=Ubuntu:Edgy/AddOnApplications&action=edit&section=8")]

---

### Post by jgf621 on 2007-01-10
Situation still exists.  I tried again as directed and get this message on RELOAD.  Significant?


W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy_universe_binary-amd64_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_edgy-updates_universe_binary-amd64_Packages)

---

### Post by MindRiot on 2007-01-10
Open System > Administration > Software Sources

The first tab displayed should be Ubuntu 6.10

Make sure all the check boxes under "Internet" are ticked.  Click close.

Open System> Administration > Synaptic Package Manager

On the tool bar, click Edit, then Search

Type acroread.  Then click Search.

Click the check box next to  acroread from the list in the right pane and mark it for installation.

Click the Apply button.

---

### Post by jgf621 on 2007-01-11
Thanks.  It gets worse.  I now get the following message:

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

Trying to RELOAD tells me that the repository is no longer available.

If someone could send me the correct text for the  /etc/apt/sources.list.d/edgy-universe.list file or tell me how to re-create it, I would be thankful.

---

### Post by Johnathon on 2007-01-22
I had exactly this problem. 

My solution?

Strip sources.list back to its very basic mains, and then remove the files being complained about. (rm /file/location/filename)(Just comment out all your extras by adding "#" to the beginning of the line)

Step by step:
Open up a terminal (Applications > Accessories > Terminal)

Type ```
sudo su
```
Enter your password, but now be VERY VERY careful. One wrong move will destroy your computer without any warnings.

now, ```
gedit /etc/sources.list
```
Add a '#' to every line that starts with "deb", except the 2 with "main" in them (these: 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted )

Now, exit gedit, back to the terminal, and we have to delete each one of the files that you're being told is corrupted.
Do a
```
apt-get update 
```
and watch for the files. 

now, type, VERY CAREFULLY
```
rm /etc/apt/sources.list.d/FILENAME
```
Replace FILENAME with the name of the file thats acting up.
Once you have rm'ed all the files, do another 

 ```
apt-get update.
```

Now, 
```
gedit /etc/apt/sources.list
```
Uncomment all the lines you commented, save, exit and do another:
```
apt-get update 
```

Hth :)

---

