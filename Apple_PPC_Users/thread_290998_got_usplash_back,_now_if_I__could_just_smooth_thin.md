---
title: "got usplash back, now if I  could just smooth things out"
date: 2006-11-01
forum: Apple PPC Users
---

### Post by seatea on 2006-11-01
I upgraded my Powermac G4( 1 GB RAM, ATI Rage 128 PF/PRO AGP 4x TMDS) to  Edgy and had a few anomalies. The first one I  noticed was the black screen after yaboot until GDM login and the  black screen at shutdown.  The Dapper usplash  had worked from start with text at startup after yaboot and at shutdown. I spent way too much time trying to get it to work, but I did get it functioning  again with text although  there are a few cosmetic glitches.

Here's what seemed to finally work for me. I had installed - reinstalled usplash and everything  usplash I could to no avail. I  reset the usplash.conf file to multiple  resolutions  and tried them all out with no success. I tried doing the  custom splash installation from the Edgy Guide How To which involves running ```
sudo dpkg-reconfigure linux-image-$(uname -r)

``` at the end with no results either. From the bug  reports, [HTML]https://launchpad.net/distros/ubuntu/+source/usplash/+bug/60621[/HTML], I  saw a comment  about re-setting  the values in usplash.conf  to:

xres=1024
yres=768 

(they had been xres=1280, yres=1024) and then running ```
sudo update-initramfs -u
```. I did this  and changed my yaboot.conf to read  append="verbose splash" , ran ybin -v and restarted. I now had the text and usplash  with  progress bar, albeit with  a few extras.

I had looked at the usplash docs and man pages, but they do not  clearly spell out the boot process and how usplash is set up. I did  see in  one part that the usplash-theme-ubuntu was referred to at 1024 x 768 resolution and this too seemed to fit  with the final steps that restored a usplash.

What  is off is that now after yaboot  when the  Edgy kernel boots, I get first, a white screen (I had always gotten this in Dapper), then a black screen with text (not seen in Dapper), then the  Ubuntu usplash with  rolling  text(similar to Dapper), then black screen  with text (not seen  in  dapper) and then a screen that is 1/3 white, 1/3 black, and  1/3 Desktop picture (also seen in Dapper) and  finally GDM login  screen. It would be nice to go straight  to usplash from yaboot and then to GDM login without  all the annoying extras. I should add that the shutdown splash with rolling  text does fine without  any  extra flashes of screen display.

I had tried setting  multiple  options in  yaboot for vga (=794, 791,or 795) which did nothing. I had tried the  video=ofonly and that didn't help either. I don't know that you need  to say "verbose splash" or "text splash" as I have read that just removing  the quiet from the  append+"quiet splash" option that seems to be standard in ubuntu yaboot.conf will restore the text.

I don't know why I got fixated on this problem. Hopefully if anyone else is bothered by  the absent usplash, maybe this information will speed up their solution to restoring  the uspalsh.

Now, does anyone have any suggestions  on  how to get rid of all the excesses in the  boot process from yaboot to GDM login?

---

### Post by Culito on 2006-11-03
I have yet to find the right combination of the kernel vga settings and usplash.conf settings.  My lcd monitor's resolution is 1280x1024, which doesn't jive, evidently.  Usplash from the command line displays perfectly, but when I boot up or shut down my monitor just says, "input not supported".
Sigh.
I have got it to display a few times, way too big, so that it was wrapping around the screen.  But I don't remember what settings were!  Off to do more tweaking...

---

### Post by seatea on 2006-11-04
My monitor resolution is set at 1280 X 1024 too. There is an interestng  link in the "How to" section  on changing  boot  resolution,  [http://ubuntuforums.org/showthread.php?t=258484&highlight=boot+resolution](http://ubuntuforums.org/showthread.php?t=258484&highlight=boot+resolution). I wasn't able  to do anything constructive with my usplash with changes in yaboot using any vga=xxx combination. I am guessing that  the  usplash.conf and the  actual resolution of  the  usplash images  is the key to using  the  bootsplash. Of  course, the video  card of  your  computer  must be taken into account.

---

### Post by agds on 2006-12-20
> **seatea said:**
> Now, does anyone have any suggestions  on  how to get rid of all the excesses in the  boot process from yaboot to GDM login?

I couldn't tell if this was what you meant, but you could decrease the values of the timeout variable(s) in your /etc/yaboot.conf.

---

