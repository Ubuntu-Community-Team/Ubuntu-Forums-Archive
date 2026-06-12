---
title: "[SOLVED] How to update program (Deluge) - need to remove old one first?"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by bluepowder7 on 2007-11-25
newbie question - when it comes to wanting to install a more recent version of a program (in my case Deluge), do i need to completely remove the current version that i have installed, or can i just let it sit there and download / install the newest version?

i currently have Deluge 0.5.4.1 installed, and a few torrents are going (slowly), but it looks like the new version (and other updates along the way) addressed some of the issues i'm seeing, so it would make sense to have Deluge 0.5.6.96 installed.  some of my torrents are only part way done (and they're kinda big), so would i have to restart them from scratch if i do this upgrade / reinstall?

---

### Post by jken146 on 2007-11-25
I don't know anything about Deluge, but if you installed it from the Ubuntu repositories (i.e. (probably) through Add/Remove, Synaptic, apt-get or aptitude) then updates are automatic, so you can either wait for the Ubuntu repos to be updated or you can uninstall Deluge and install a newer version that you get from somewhere else.  Here's a guide to installing things: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

I should also point out that slow torrents are often not due to the client you have installed, but on things like firewalls, forwarded ports, trackers etc.

As for restarting your downloads, you probably won't have to but it depends on if Deluge has a resume feature (most BT clients do).

Personally I use Azureus with no problems.

---

### Post by ubuntu27 on 2007-11-25
Let's see if I understood your dilemma.

1) You are using Deluge which was installed using the repositories (e.g. Synaptic, apt, aptitude)

2) You want to install the latest version from an outside source such as [Deluge website]("http://deluge-torrent.org/") or [GetDeb]("http://www.getdeb.net/")

3) you are currently downloading some files with deluge (You are not done downloading)



It is better if you wait until all your downloads has been finished. 
I don't know about deluge, but when I used to use the original Bittorrent client. I was downloading some file and decided to update the client also. My downloads was eliminated.

So. Wait until you finished downloading.
And UNINSTALL Deluge

and then you can install the current version of Deluge.

have a nice day with Deluge :)

---

### Post by philinux on 2007-11-25
you will have no doubt got the deb file direct from deluge website.

i seem to remember that yes you uninstall before installing new version but all your config files and part torrents are stored in your home folder so should be no prob.

I think there are instruction on there website about upgrading to latest version.

---

### Post by bluepowder7 on 2007-11-25
right, it was originally installed via Synaptic.  so, it sound like i should UNinstall it first and then install a newer version (which isn't on Synaptic but i can download the .deb package directly from the Deluge site).

now, when it comes to removing a program with the intention of installing a newer version, which uninstall option should i select in Synaptic - remove or complete remove?  i'd like for the new install to be as clean as possible, i don't mind redoing some of the preferences (there aren't many in this case), but i DON'T want to lose the torrent progress so far (so, if i've downloaded 1.2G out of a 2.4G file, i sure as heck don't want to have to restart that download from the beginning)


EDIT - ok, looks like two replies came up as i was typing this post.  yeah, the instructions on the Deluge site seem to be about installing, but it sounds like they assume "install because you never had it in the first place".  if that was the case, it looks like it would be relatively easy.  i checked my torrents - one is gonna be done in 5mins, one is just barely started (800megs out of 3.4gigs), and one is half done.  hmm...  losing that 800meg chunk wouldn't be THAT bad, but the other is 1.2G out of 2.4G, so losing that would suck (and it's a slow torrent, only 1 or 2 seeds)

---

### Post by jken146 on 2007-11-25
As it's the same program I'd wager the dependencies are probably the same (or nearly) so it doesn't really matter.  Use completely remove if you like and it shouldn't hurt you.

---

### Post by bluepowder7 on 2007-11-25
update - ok, waited until one of the torrents was done, and left that other (800megs out of 3.4gigs) interrupted.  uninstalled the existing deluge completely, downloaded and installed the new one, and things work perfectly!  recognized my previous settings of ports, folders, and progress (even though it was marked for complete removal including config files), and is adding to the existing torrent as we speak.  cool!!!  easier than i thought.

---

