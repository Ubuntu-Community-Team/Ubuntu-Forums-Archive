---
title: "compiz fusion cube plugin"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by nathan1936 on 2007-12-25
Hi, I was just needing to know how to work the compiz fusion cube. How do you zoom out so you can actually see/move the cube around? I can rotate it, but I am not sure how to zoom out and look around. So if there is a key combination, or a package I need, please explain. 
Also how do I select what images go on the top and bottom of the cube? I didnt see any place to set that...

Thanks in advance.

---

### Post by shareMenaPeace on 2007-12-25
Middle mouse button i think, also with ubuntu-tweak.com you can assign more nice windows options ... with 

hold middle mouse than press SPACE + ALT you can freez the camera position

---

### Post by kdarkentity on 2007-12-25
control+alt+left click 

Is that what your looking for?

---

### Post by nick_h on 2007-12-25
Yes, click the middle mouse button on the desktop and then drag to rotate the cube.
You have to select Desktop Cube and Rotate Cube in the Advanced Settings.
Desktop Cube->Appearance->Cube Caps lets you set the images for the caps.

---

### Post by LinuxIsInnovation on 2007-12-25
To set the zoom parameters, open ccsm, goto Rotate Cube. Zoom is the last option on the page.
Ctrl+Alt+Left/Right arrow keys switch to adjacent faces of cube.
Also ccsm->Desktop cube->Appearance->Skydome for a background image.
Use a large background image for an animated skydome but make sure to check the Animate Skydome checkbox under the Skydome options.

---

### Post by nathan1936 on 2007-12-25
Ok, well I made it work, but... lol im such a noob.
What is ccsm?
and skydome?
lol I have compiz fusion, but are those extra things I need?

---

### Post by nathan1936 on 2007-12-25
Ok I guess I'm not a total noob I got it running :) , Now one more thing... Does anyone know how to set a screensaver as your background? If anyone knows of any plugin please tell

---

### Post by LinuxIsInnovation on 2007-12-25
ccsm: Compiz config settings manager

A skydome is the background you see when the cube is zoomed out.
[http://i15.tinypic.com/72rru5k.png](http://i15.tinypic.com/72rru5k.png)
This is my cube with the animated skydome.

---

### Post by RomeReactor on 2007-12-25
Hi. CCSM is CompizConfig-Settings-Manager; yo can find it in Synaptic; or to install it from the terminal:
```
sudo apt-get install compizconfig-settings-manager
```
Once it's installed you can find it in "System->Preferences->Advanced Desktop Effects Settings"; there you will be able to enable or disable more plugins such as the Skydome, which is a background image for the cube.

EDIT: Too slow...

---

### Post by barbedsaber on 2007-12-25
Two questions, is there a database of good skydomes to chose from, I am getting sick of the gray reflection which I know I can change, but I want a skydome. second, how do you get the windows to stick out on the cube. you can see the windows layers clearly.
thanks.

---

### Post by nathan1936 on 2007-12-25
1. How do you make the windows appear to stick out, on the cube [in layers], like they do on yours? Mine appear to be flat against the cube.
2.How would I make the entire cube appear transparent [opaque] when revolving around it? Can I make the desktop opaque?
3.How do I set a screensaver as the background?

Thanks for all the attention to my questions! I appreciate your patience. :KS

---

### Post by barbedsaber on 2007-12-25
to make the cobe transparentwhile you rotate it, clikc system, admin, advnace desktop effects,, desktop cube (the image, not the tick box), transparent cube, and drag the slider bar down.

hope thats helpfull.

---

### Post by RomeReactor on 2007-12-25
> **barbedsaber said:**
> Two questions, is there a database of good skydomes to chose from, I am getting sick of the gray reflection which I know I can change, but I want a skydome.

Hi. If I remember correctly Wikipedia had a very good article on panoramic photography with many pictures, but all I could find now is [this entry]("http://en.wikipedia.org/wiki/Panorama"); in any case, there are skydome images in [Compiz-Themes]("http://www.compiz-themes.org/index.php?xcontentmode=6110"), and [The Open Directory]("http://www.dmoz.org/Recreation/Travel/Image_Galleries/Panoramic//") has links to sites with panoramic images.

Hope this helps.

---

### Post by barbedsaber on 2007-12-25
thanks, but I can't get it to work with skydomes, but can someone PLEASE help me with sticking out windows.

---

### Post by JillSwift on 2007-12-25
The floaty windows is part of the extra plugin package described here:
[http://ubuntuforums.org/showthread.php?t=620000](http://ubuntuforums.org/showthread.php?t=620000)

---

### Post by tonycm1 on 2007-12-26
How do i zoom out in the desktop cube? I've been trying this for about 15 minutes on my laptop with my touchpad... any ideas?

I know how to rotate the cube (ctrl+alt+left mouse button+moving mouse around), but dont know how to zoom out so i can see the entire cube... :confused:

---

### Post by tonycm1 on 2007-12-26
bump.

---

### Post by sailor2001 on 2007-12-26
in terminal: ccsm and click zoom desktop, increase slide

---

### Post by tonycm1 on 2007-12-26
I've moved the zoom factor all the way to the right (at 3.000), but when I go to rotate my cube, I don't know how to zoom out so that I can see the whole cube... any ideas?

---

### Post by overdrank on 2007-12-26
> **tonycm1 said:**
> I've moved the zoom factor all the way to the right (at 3.000), but when I go to rotate my cube, I don't know how to zoom out so that I can see the whole cube... any ideas?

Hi under rotate cube in CCSM, zoom in the general tab. And while you are there in CCSM make sure you have the desktop cube checked.

---

### Post by tonycm1 on 2007-12-26
Double checked that... moved slider all the way to the left and right, no difference....

It seems as though i'm "IN" the cube, and not outside it... here's a screenshot of what I see:

[http://img150.imageshack.us/content.php?page=done&l=img150/3872/screenshothb1.png](http://img150.imageshack.us/content.php?page=done&l=img150/3872/screenshothb1.png)

---

### Post by loudnlownoma on 2007-12-26
Looks like you are using the Inside Cube option.  If you open CCSM and go to the cube options, in the same panel as the Skydome options I believe, there is an option for Inside Cube.  Uncheck that.

EDIT: Sorry if any of the wording or locations are off...posting from work, where I'm stuck with XP  :(

---

### Post by tonycm1 on 2007-12-26
Oh man do I feel dumb, I didn't even notice that was checked on. Thank you so much :P

---

### Post by loudnlownoma on 2007-12-26
No problem.  As simple as it seems, I've done similar a great number of times..lol.  Sometimes it just takes that outside pair of eyes to say "Hey, ya missed something"  Hehe.

---

