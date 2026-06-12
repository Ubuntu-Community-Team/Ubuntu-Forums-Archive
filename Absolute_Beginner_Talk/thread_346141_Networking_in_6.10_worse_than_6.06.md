---
title: "Networking in 6.10 worse than 6.06?"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by jonandrews on 2007-01-25
Can anyone help me understand this?

Whilst developing a procedure to configure networking between Ubuntu and Windows pc's, I stumbled on some networking degredation between 6.06 LTS and 6.10. By repeating clean installations of both versions, I have confirmed my observations, as follows:

On virgin installations of 6.06,  In Places > Network Servers,  a 'Windows Network' icon is displayed.

D/clicking on it will take you to [the name of your windows network], in my case mshome

D/clicking on mshome will display all the Windows pc's currently on my network, and their icons lead to  their shared folders and files.

You can also print from the Ubuntu PC 6.06 (using Open Office) onto a printer attached to a Windows PC by just installing a network printer in Ubuntu.


On virgin installations of 6.10, Places > Network Servers,  'Windows Network' is displayed correctly.

However, when clicking to go to the next level down, instead of a normal networking icon for mshome, a grey square folder Icon is displayed.

When clicking on this to go to the next level down, an error is returned:

'Couldn't display "smb:///mshome"   The location is not a folder'

Then, sometimes, by pressing reload, ctl-R, the correct icon will appear, and responds correctly, displaying individual pc's on the network,

The same problem then occurs with the individual icons for the pc's on the network.

Bizzarly, different pc icons can be made to flip between the correct icon & the grey square icon by pressing reload, ctl-R.  When grey squares, the icons for the pc's return the same error as above.

Finally,  printing from the Ubuntu PC 6.10 (using Open Office) onto a printer attached to a Windows PC by just installing a network printer in Ubuntu does not work, even though the printer shows as present & 'ready' in System > Administration > Printing.   Open office only shows 'Generic Printer' available.

---

### Post by ftabor on 2007-01-25
I don't have a solution, but I can confirm the same results here.

---

### Post by hopestorm on 2007-01-25
Both my wireless and wired connections are gone, and I can not install any package suggested to reset the network conection.

I don't know what I should do now, reinstall the whole system?

---

### Post by steve.horsley on 2007-01-25
I confirm the problem. If you right-click the icon, you can copy the link from the link tab and paste it into the location bar, and that works.

---

### Post by jonandrews on 2007-01-26
Thank you all for your comments.

So, for me, the conclusion is obvious, as I do not have the skill to do much 'under the bonnet'. 

I will stay with 6.06, which works fine on my windows network, and evaluate releases beyond 6.10 as & when they arrive.

Finally, has anyone come across a summary of  improvements between 6.06 & 6.10 described in terms of benefits to an 'ordinary' desktop user? 
(as opposed to a list of file names & services that I don't understand). 

I would like to know what I'll be missing....

---

