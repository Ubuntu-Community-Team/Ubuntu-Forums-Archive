---
title: "OO base + java + headache"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by geokok1981 on 2006-10-29
I was having problems creating forms in OObase through the wizard so I thought of using Sun java instead of the default FSF version provided.
I installed through "add-remove programs" the JRE 5.0 as well as the plugin for the broswer. Now I am having even worst problems in OO base (the wizards wont even start now). I cant deactivate java completely cause OO needs it, I cant roll back to the FSF version which even if I could is useless (the original problem was that with the FSF version the forms wizard wouldnt do anything at all once I hit finish button) and generally I am completely stuck.....

What can I do to fix OO+java and make sure I havent broken my system?

---

### Post by geokok1981 on 2006-10-29
I un-installed java and re-installed through automatix2...
I even reinstalled oo base....
No good..The wizard for  the form creation never starts....

Any chance this is a bug? 
Could it possible for ubuntu to allow the user to mess up it application so easily?
Is ot possible to be so d***mn hard to do something as simple as creating a form with the wizard? I mean I ve seen tutorials on the web using it but they all were on windows machines......

---

### Post by geokok1981 on 2006-10-30
I checked the java -version through terminal and it is the same as the one selected in OO. So I guess it is not a conflict problem.

 Can someone at least tell me how to completely get rid of java and do the proper steps again, in hope that it might work?

---

### Post by The Mekon on 2006-10-30
I got OO Base working using the following [tutorial]("http://sheepdogguides.com/fdb/fdb1install.htm").

The important section is:

"Start an Open Office text document. (Yes... text document!)
Click on the menu entry Tools
Click on the sub menu entry Options
If the "OpenOffice.org" heading has a + ion front of it, click
     on the + to make it a -, and display the tree of sub-options
Click on "Java", and hold your breath! Don't be alarmed if no JAVA RTEs show
After a moment or two, you should see one or more RTEs.
Select the one with a version id starting 1.5... or higher.
Close everything.
Try Base again!"

Brian

---

### Post by geokok1981 on 2006-11-06
Already tried that. I am currently using Sun Java 1.5.08.
No luck. With FSF java the form wizard starts but wont finish.
WIth SUN Java it wont even start.
Other wizards work fine.
I found a bug report for this at launchpad but is still unconfirmed.
This a major bug which seems to be ubuntu-specific.
It's a shame that the main office suite has such a huge flaw in ubuntu when windows users claim it works fine for them....

---

