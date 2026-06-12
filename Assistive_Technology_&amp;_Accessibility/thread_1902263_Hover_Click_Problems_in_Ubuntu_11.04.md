---
title: "Hover Click Problems in Ubuntu 11.04"
date: 2011-12-30
forum: Assistive Technology &amp; Accessibility
---

### Post by annaek on 2011-12-30
[SIZE=2]I'm having trouble with the hover click function in Ubuntu 11.04.  I go to the mouse settings dialog and select "initiate click when stopping pointer movement" on the accessibility tab.  I've also selected "choose type of click beforehand," and "show click type window."  I click close on the dialog box and attempt to hover over a button.  Nothing happens.  Additionally, the click type window does not appear. I've tried hovering over multiple types of objects with no results.  I've also tried using Ubuntu Classic instead of Unity.  Hover click doesn't work there either.[/SIZE]
 

 

 [SIZE=2]I'm running Ubuntu 11.04 on an Asus Eee PC netbook.  Obviously, I'm interested in a solution to this problem, but I'd also like to know whether it's a known issue that is likely to repeat itself on another computer.  I am considering putting Ubuntu 11.04 on my main computer, and I'd like to know whether hover click is likely to cause me problems there, too.  Thanks![/SIZE]

---

### Post by annaek on 2012-01-03
I've mostly solved my own problem.  I don't really understand why, but the following procedure worked for me: 
-login using Ubuntu Classic 
-Go to the system menu.  Select preferences, assistive technologies.   
-In the Assistive Technologies Preferences window, select "Enable assistive technologies" and then click on "mouse accessibility." 
-In the mouse preferences window, select the accessibility tab.  Check the box for "initiate click when stopping pointer movement." 
-Close those windows and return to the desktop.  Right click on the gray panel At the top of the screen and select "Add to Panel..." Select Dwell Click Applet from the list. 
-The dwell clicker should now be functional.  Hover over the mouse icon on the panel applet to enable/disable it. 
-It is now possible to login using Unity, and the dwell clicker still works, but the applet is not displayed.  Additionally, if I close the click selection window, I have no way of choosing a click type. 
I'm pretty satisfied with this solution (as long as I stick with Ubuntu classic), and I did go ahead and put 11.04 on my main computer.  

I'm now experiencing one other problem.  Sometimes, when I boot up my computer, the dwell clicker simply doesn't work.  The applet is there, but no click is generated when I dwell.  I can fix this problem by opening the accessibility settings and toggling the check box for "initiate click when stopping pointer movement," but that takes a decent bit of mousing and clicking, which is hard for me.  Does anyone know why this is happening or how it might be prevented?

---

### Post by Dreamer Fithp Apprentice on 2012-02-28
> **annaek said:**
>  . . .   I can fix this problem by opening the accessibility settings and toggling the check box for "initiate click when stopping pointer movement," but that takes a decent bit of mousing and clicking, which is hard for me.  Does anyone know why this is happening or how it might be prevented? . . . Not I, but I do have a suggestion that you might want to pursue. Try to find the command line equivalent of what you are doing to "fix" it in a GUI. Then you can just put it in a script and point a launcher at the script. Then you'd only have to click the launcher. One precaution though, it might be hard to find the proper commands because that is probably a gnome thing and the gnome people changed just about everything, not just in the gui controls but in the command syntax as well, in the new gnome 3, so anything you find written on the subject may well be out of date. If nothing else, I suggest you email the gnome people. Surely someone there would be decent enough to take 5 minutes to send you an appropriate script. It is the least they could do, considering how many people's scripts they broke, and how much carefully written tutorial material is now useless because they didn't bother to maintain backward compatibility. It is a work around kludge, but perhaps better than nothing. 

You sound like you have some experience with this type of thing. Have you run across how to get drag lock to work on a trackball button?

---

### Post by annaek on 2012-03-13
That's an interesting idea.  I'll have to look into it when I have more time.  I've never tried to write a script like that before. 
 
I actually have very little experience with this, and I'm afraid I wouldn't know where to start with a drag lock.   I'm just a (fairly new) user trying to make my computer work for me.  (Though, now that I think about it, the dwell clicker does incorporate a click and drag functionality.  You might want to see if it would meet your needs and/or look at the source to see how it's implemented.  Just a thought.)

---

### Post by Dreamer Fithp Apprentice on 2012-03-13
Thanks. I tried it. I couldn't get it to work at all for some reason. Nothing like "dwell click applet" appeared in my list of choices to add to the panel, nor in synaptic. It's not a major big deal. Mainly I just need to get a new trackball. Mines about worn out and I was just looking for ways to put the purchase off a little longer. Thanks though.

---

### Post by zarkasi on 2012-06-21
hmmm, i am using ubuntu 12.04, and suddenly my mouse's setting changes to initiate click, but there is no assistive menu. how can i remove this hover problem? maybe somebody knew the solution via terminal?

---

### Post by HuttonIT on 2012-06-22
I have just aquired a very nice Lenovo X1 Carbon and installed a SSD HD then loaded up Ubuntu 12.04 LTE.  Everything works fine but the Right Click on the Touch-pad.  The Right Click on the keys above works fine.  Even the click on the centre of the pad works and two finger scrolling etc...  
Here is a very strange thing tough.  Using VirtualBox with Windoze XP the right click works.  This leads me to believe that the issue is specificity no action is associated with the right click on the pad in Ubuntu.

For those who have not had hands on an X1 the Touch-Pad is a flat pad with no buttons as normal.  The pad has sensors under the bottom edge which operate as the buttons.  The buttons above are for use with the Track Point Lenovo and IBM have had for years.
[IMG]http://www.notebookcheck.net/typo3temp/pics/014c437f0e.jpg[/IMG]
Any Geniuses out there able to help would be wonderful.

---

