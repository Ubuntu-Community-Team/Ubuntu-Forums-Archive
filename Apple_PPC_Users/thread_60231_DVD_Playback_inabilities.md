---
title: "DVD Playback inabilities"
date: 2005-08-26
forum: Apple PPC Users
---

### Post by johnnyspflame on 2005-08-26
I have tried everything in attempt to be able to use DVD playback on my PBook G4, but every time i launch Totem or xine, it says it cant read it. I've checked and all of the libdvd* files are current. Does anyone have any suggestions.

---

### Post by codejunkie on 2005-08-26
[QUOTE=johnnyspflame]I have tried everything in attempt to be able to use DVD playback on my PBook G4, but every time i launch Totem or xine, it says it cant read it. I've checked and all of the libdvd* files are current. Does anyone have any suggestions.[/QUOTE]

[http://powerpc.ubuntuguide.org/#dvdplayback](http://powerpc.ubuntuguide.org/#dvdplayback)

---

### Post by johnnyspflame on 2005-08-27
Yeah, Generally before i'd waste forum time, i'd attempt the suggested methods of fixing the problem. I have already tried that, and still havent had any luck.

---

### Post by codejunkie on 2005-08-27
[QUOTE=johnnyspflame]Yeah, Generally before i'd waste forum time, i'd attempt the suggested methods of fixing the problem. I have already tried that, and still havent had any luck.[/QUOTE]
if you have already enabled the extra repos and installed libdvdcss2 you also need to install totem-xine because the version of totem included with ubuntu is crippled because of copyright restrictions also install the gstreamer0.8 plugins.

---

### Post by johnnyspflame on 2005-08-28
As it turns out i dont think i have libdvdcss2 installed, however i havent been able to find it, in the synaptic package manager. so im curious as to where to obtain that. I downloaded the Totem-xine, though the video is incredibly choppy and then cuts out with a message stating that an error occured and do i have Libdvdcss2 installed. obviously then i dont. 
Thanks for the totem-xine suggestion, it'll at least play now, just gotta fix the choppiness.

---

### Post by codejunkie on 2005-08-28
[QUOTE=johnnyspflame]As it turns out i dont think i have libdvdcss2 installed, however i havent been able to find it, in the synaptic package manager. so im curious as to where to obtain that. I downloaded the Totem-xine, though the video is incredibly choppy and then cuts out with a message stating that an error occured and do i have Libdvdcss2 installed. obviously then i dont. 
Thanks for the totem-xine suggestion, it'll at least play now, just gotta fix the choppiness.[/QUOTE]
you have to follow this guide [http://powerpc.ubuntuguide.org/#extrarepositories](http://powerpc.ubuntuguide.org/#extrarepositories) to add the extra repos to your /etc/apt/sources.list file and then libdvdcss2 will be in there hope this helps.

---

