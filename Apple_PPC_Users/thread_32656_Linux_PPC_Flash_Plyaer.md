---
title: "Linux PPC Flash Plyaer"
date: 2005-05-08
forum: Apple PPC Users
---

### Post by JaceMan on 2005-05-08
Is there a way to install Macromedia's Flash Player for Linux on a PPC?  I have tried both installing via apt as well as manually from macromedia's site.  They don't seem to like it.  Is there a workaround?

Thanks...

---

### Post by craks on 2005-05-08
no ppc version macromedia flash player, but gentoo user use it under qemu

---

### Post by calum on 2005-05-09
[QUOTE=JaceMan]Is there a way to install Macromedia's Flash Player for Linux on a PPC?  I have tried both installing via apt as well as manually from macromedia's site.  They don't seem to like it.  Is there a workaround?
[/QUOTE]

There's no PPC version I'm afraid, their Linux version only works on x86 machines.  There are a couple of open source alternatives, like [swfdec](http://www.schleef.org/swfdec/).

---

### Post by JaceMan on 2005-05-09
[QUOTE=calum]There's no PPC version I'm afraid, their Linux version only works on x86 machines.  There are a couple of open source alternatives, like [swfdec](http://www.schleef.org/swfdec/).[/QUOTE]

Thanks, I'll give swfdec a try (what are some of the other alternatives?) as the gentoo option using qemu was WAAAAAAAAAAAAAAAAAY over my head.

---

### Post by calum on 2005-05-09
[QUOTE=JaceMan]Thanks, I'll give swfdec a try (what are some of the other alternatives?) as the gentoo option using qemu was WAAAAAAAAAAAAAAAAAY over my head.[/QUOTE]

[gplflash](http://gplflash.sourceforge.net/) is another.  Haven't used either of them on PPC linux though, so can't speak for how easy they are to get up and running, or how functional they are.

---

### Post by DJ_Max on 2005-05-09
For more reference, [http://ubuntuppc.info/AddOnApplications/FlashAndSWF](http://ubuntuppc.info/AddOnApplications/FlashAndSWF)

---

### Post by chascon on 2005-05-11
I'm sure I've answered this one many times.

$ apt-cache show swf-player
Package: swf-player
Priority: optional
Section: universe/utils
Installed-Size: 152
Maintainer: David Schleef <ds@schleef.org>
Architecture: powerpc
Source: swfdec0.3
Version: 0.3.2-2
Depends: libart-2.0-2 (>= 2.3.16), libc6 (>= 2.3.2.ds1-4), libglib2.0-0 (>= 2.6.0), libgtk2.0-0 (>= 2.5.6), libmad0 (>= 0.15.1b), libsdl1.2debian (>> 1.2.7-0), libswfdec0.3, libxt6 | xlibs (>> 4.1.0), zlib1g (>= 1:1.2.1)
Filename: pool/universe/s/swfdec0.3/swf-player_0.3.2-2_powerpc.deb
Size: 30108
MD5sum: 09bc46e08404ca1fce717f98eb4a88d7
Description: SWF (Macromedia Flash) player
 A GTK+ and SDL based player for Macromedia Flash animations.  Includes
 a Mozilla plugin, that embeds the player into Mozilla-based browsers,
 in order to allow seamless viewing of Flash animations in web
 pages.  Includes a GdkPixbuf loader, so that SWF animations can be
 used seamlessly as images in Gtk+ applications.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

---

### Post by chascon on 2005-05-11
I just tried the swf-player, although I knew about from before.
I did a:
sudo apt-get install swf-player

Although it works, but not perfectly compatable with flash at 2kool4radio.com , two instances of it, one in mozilla and another in firefox, take up more than 50% of my cpu.  This is quite noticable. as a big slowdown in comp operations.  So I removed it.

---

### Post by JaceMan on 2005-05-12
I was able to install swf-player since it is available via apt-get.  I haven't gotten the other suggest ones to install because I'm too stupid I guess.

And unfortunately, I can't find much that swf-player will play either.

*sigh*

---

### Post by JaceMan on 2005-05-12
[QUOTE=DJ_Max]For more reference, [http://ubuntuppc.info/AddOnApplications/FlashAndSWF](http://ubuntuppc.info/AddOnApplications/FlashAndSWF)[/QUOTE]

I actually got it to install - (used synaptic to apt a ton of stuff from the Development section of the repositories) so it seems... but I don't understand how to get the plugin feature to work.

I read the readme, but I couldn't really comprehend how to make the plugin work for mozilla firefox.

Could you dummy the plugin aspect down for me please?

---

### Post by ipixel on 2005-05-15
For those of us using KUBUNTU on PPC: will the flash player work for Konqueror? Should we even bother? Has anyone tried? - or do we have to instal Firefox?

---

### Post by chascon on 2005-05-17
[QUOTE=][/QUOTE]
 > I was able to install swf-player since it is available via apt-get. I haven't gotten the other suggest ones to install because I'm too stupid I guess.

And unfortunately, I can't find much that swf-player will play either
All I did was to apt-get it.  Restarted mozilla and firefox and it worked.  No configuring, although you might want to look over you preferences and enable plugins or something like that but didn't.  I found it worked simply on the restart of those browsers, meaning it didn't work on a browser you had open while you apt-get installed swf-player.

About it working with konqueror, never tried it. Haven't used kde for about a year.  Why not try swf-player and post back your results.  If something finds swf-player taking up a lot of cpu please confirm as I'm thinking of filing a bug report on it.

---

### Post by breakdaze on 2005-10-08
DJ_Max: That link is 404ed, try: <a href="http://ubuntuppc.info/index.php?node=17">http://ubuntuppc.info/index.php?node=17</a>

I just tried to do the sudo apt-get install libflash-mozplugin and restart Firefox. The browser indicates that the plugin is installed, but I went to a site with flash and it said I needed the plugin still.

I haven't tried everything on the other posts.

I was searching around and reading about it, and as it turns out that particular plugin only works for older Flash (5 and below, I think). There is a project for a second generation plugin rewritten from scratch, but it is way upstream and needs to be compiled from source.

Of course a Windows under Linux emulator like qemu may work, but the CPU usage for emulation is probably pretty instensive, I would guess.

Search these forums, there is a petition to have Macromedia make one for Linux under Powerpc.

---

