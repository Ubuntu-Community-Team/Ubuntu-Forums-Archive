---
title: "[B]Mplayer not working in firefox[/B]"
date: 2007-04-10
forum: Absolute Beginner Talk
---

### Post by alexlex on 2007-04-10
**Mplayer not working in firefox**
ok this is my second post.(different problem)
I have installed Mplayer and the proper codecs (via [www.howtoforge.com](www.howtoforge.com) (ubuntu the perfect desktop) setup instructions). At the Point that i installed mplayer everything worked great. I was able to listen to dc101.com live stream and hot995.com live stream. but after the first reboot it no longer worked. the video advertisement that plays in the beginning works but when it switches to live stream nothing happens Mplayer does not come up in the window. I have tried uninstalling Mplayer and reinstalling it but nothing. I have found not threads with this same problem. any help would be great. thanks.

P.S. I am running Ubuntu 6.10 Edgy.

---

### Post by garybrlow on 2007-04-10
You need the Mplayer Mozilla plugin. Or if you don't want to use that you can change the default file associations in firefox to open particular video file types like rm wmv etc. to open in Mplayer.


Cheers!!!


GaryBrlow :biggrin:

---

### Post by alexlex on 2007-04-10
> **garybrlow said:**
> You need the Mplayer Mozilla plugin. Or if you don't want to use that you can change the default file associations in firefox to open particular video file types like rm wmv etc. to open in Mplayer.


Cheers!!!


GaryBrlow :biggrin:

I do have the plugin but still not working.
i like the other option you talked about thats an awsome idea i think that would work great for me i am not to picky about how something works as long as it it works i don't care. thanks for the reply but if it is not to much of a problem do you think you could give me a steb by step walkthrough of how to do that?
thanks in advance

---

### Post by garybrlow on 2007-04-10
1)Click Edit on the Firefox Menu Bar, then Preferences.
2)The Preferences Dialog Box should be open now. Click on the content icon (the one that looks like globe) to access the content tab. 
3)Go to the File Types sections and click on the Manage button.
4)Another dialog box will open, this is the Download Actions Dialog Box
5)You should now see a table of file extensions and their default Actions. Choose the particular file extension you want to change. Ex. AVI, the whole avi row should be highlighted now. Click on change action.
6)Another dialog box opens allowing changes in action settings. Default setting is set to Use this Plugin to change select Open them with default application and provide the executable command/path to a particular application you want to use. Ex. for Mplayer its gmplayer without path since it is executable from any location.
7)This will open the file in a separate application window not embedded in the web page.
8)Take note not all files will be playable in Mplayer. Some players handle particular file types like windows media player streaming better than Mplayer.

Cheers!!!

GaryBrlow :biggrin:

---

