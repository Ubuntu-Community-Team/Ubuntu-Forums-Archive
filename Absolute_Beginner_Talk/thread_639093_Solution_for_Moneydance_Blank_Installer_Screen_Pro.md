---
title: "Solution for Moneydance Blank Installer Screen Problem"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by m9ke on 2007-12-12
This won't help you if you have problems installing Moneydance because of Java problems or 'cant start the installer' problems.  

I worked thru those and got the installer running. However it showed only a blank screen.  There is a caution on the Moneydance website that searching for Java can take a long time, so I left alone for a long time, but nothing ended up happening.

Here is what I did to solve the Moneydance blank installer screen problem.  I am running Fiesty 32-bit with an nVidia video card.  YMMV.

I changed the following, which eventually led to the previously blank Moneydance installer screen working as expected: 

1. System->Preferences->Desktop Effects:  Disabled Desktop Effects (Windows Wobble When Moved and Workspaces on a Cube)

2. Right-clicked -> Properties-> Permissions tab on the downloaded .sh file (moneydance_linux-x86.sh) and changed all the permissions to both Read and Write. Also checked Allow Executing Files as Program check box. 

Neither 1 nor 2 immediately solved the problem but I left them as described while I looked further.  Then I did:

3. System->Preferences->GL Desktop: Unchecked the Enable GL Desktop checkbox

*bingo* it worked.  I am not entirely sure that each of these is needed to fix the problem, but I did them all and it worked.  

BTW, the Moneydance installer tries to install in /usr/local and in /usr/local/bin which are owned by root.  If you get this far and get a "You don't have permission to write there" error, re-run the installer script in the terminal as sudo.

Hope this helps,
m9ke

---

