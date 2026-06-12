---
title: "No DVD play Via mplayer, xine, VLC"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by viplayday on 2007-09-29
Hello,  I have been trying to make my DVD play back work and my sound work for about 12 hours now. I have n=been trying to collect plugins, I don't understand the repositories thing.

---

### Post by rickycodie on 2007-09-29
under system select administration, then synaptic package manager.

press search and search for 

gstreamer

in the selector menu look for 

gstreamerplugins good, gstreamerplugins bad, and gstreamerplugins ugly

---

### Post by RomeReactor on 2007-09-29
Hi. Let's start with the repositories: they are basically pools of software located in a particular server; by default, Ubuntu Feisty (7.04) comes with 4 such pools: Main, Restricted, Universe and Multiverse (for a detailed explanation, [read this]("https://help.ubuntu.com/community/Repositories/Ubuntu")). To get software that is not in the repositories that come enabled by default, you need to add more repositories; so to enable DVD playback, you often hear that you need to add or enable the Medibuntu repositories, which is where the necessary libraries for DVD playback are located. Before you add them, [read this]("https://help.ubuntu.com/community/RestrictedFormats/") to learn why those packages are not available by default in Ubuntu. If after reading that, you agree to install them, [look here]("http://ubuntuforums.org/showpost.php?p=3399733&postcount=8").

What the instructions in the last link are telling you to do is:

1.- Add the repositories to a file called **sources.list**, which is where the package managers look for information regarding which repositories are available to them;

2.- Get the gpg key (to authenticate the repository), and do an update of the package managers' information about the repositories (so they are 'made aware' that new packages are at their disposal); and

3.- Install the needed libraries and codecs to play most media.

Hope this helps.

---

