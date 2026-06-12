---
title: "Puzzling Printing problem in Open Office"
date: 2007-05-14
forum: Absolute Beginner Talk
---

### Post by neotasic1 on 2007-05-14
Feisty 7.04 - I have opened a MS Word document in Open Office and tried to print to a HP Laserjet 4 connected  on a network.  Document is sent to printer but chokes at this stage, as the printer insists on printing in Letter _not_ A4 which is the only paper loaded - don't generally use Letter in Australia - A4 is the defacto standard downunder.  

Here's the weird bit.  Printing a test page through System>Administration>Printing generates no problems.  Printing through CUPS via Firefox>Localhost:631 and printing a test page generates no problems.  All the printer settings everywhere (CUPS, etc/papersize, System>Admin>Printing - I assume this is the Gnome print manager) indicate the printer is set up for A4.  Hell if I produce my own document in OO it prints fine - even if I save it in MS word XP format.  The original document prints fine on the same printer if I go through Windows.  But if I get sent a MS Word document from somewhere else (that was created in MS Word), and try to print it in Linux through OO it chokes.  

I can work around this by copying and pasting the entire document into a new OO document - whereupon it also prints perfectly (cos I don't want to boot Windows just to print a word document - over the last month since installing Feisty I don't want to boot XP at all - I have become a Linux believer), but needing this workaround seems a bit clumsy.  Has anyone come across this before, and do any of the more experienced users have any light to shed on this or any suggestions to offer.  Can anyone reproduce this or am I the only lucky person afflcted with this nuisance.

---

### Post by Jason Pettitt on 2007-05-14
I've had similar fun recently. First part of the solution is to check the default system settings for your printer. Go to the **System menu **>> **Administration** >> **Printing**. Right click on your printer and choose **Properties** and then find the **Paper** tab in the properties window and make sure it's set to A4. It'll be worth your while checking your other printer settings while your here.

The next thing you need to know is that OpenOffice saves individual printer settings with each document, so you'll still be trying to print Letter size for a while. Open the offending document and change the printer settings **File**>>**Printer Settings...**>>**Properties...** and make sure everything is set up correctly. Then save the document (you may need to do **Save As...**) so the new printer settings stick.

Hope this helps, Jason

---

### Post by neotasic1 on 2007-05-14
> **Jason Pettitt said:**
> I've had similar fun recently. First part of the solution is to check the default system settings for your printer. Go to the **System menu **>> **Administration** >> **Printing**. Right click on your printer and choose **Properties** and then find the **Paper** tab in the properties window and make sure it's set to A4. It'll be worth your while checking your other printer settings while your here.

The next thing you need to know is that OpenOffice saves individual printer settings with each document, so you'll still be trying to print Letter size for a while. Open the offending document and change the printer settings **File**>>**Printer Settings...**>>**Properties...** and make sure everything is set up correctly. Then save the document (you may need to do **Save As...**) so the new printer settings stick.

Hope this helps, Jason

Thanks for the response, but unfortunately not - that was the weird bit - everything is set up correctly, saved etc, but even though OO believes this document is A4, it insists on printing it in Letter.  What is really strange, is that the original document was sent to me by a friend who would never print in Letter either.  It's not a problem for anything but  Word files, created in MS Word, and I do have a workaround - I just wondered if it was a known bug.  Thanks for your reply in any case.:)

---

