---
title: "faxing document over ext modem ?"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by SirJ77 on 2007-09-27
I'm looking to fax a document (rtf, doc, pdf, I don't really care what format it has to be, as openoffice can do just about any doc format), over my external modem.  
I use to do this with winfax/windows without any problem, but what few references I can find, linux programs appear to be looking for an tiff file.  Is this correct?
At the moment I have efax and the gui frontend installed.
If tiff is really the only way to do it, then fine, how do I convert a rtf or doc file into a tiff file?
I'm running xubuntu 7.04.

---

### Post by frrobert on 2007-09-27
I am not in my office and I'm not at my own PC so I can't give you detailed instructions.

If you look in the documentation for efax it explains how to set up a printer queue that efax will monitor.  You then tell efax to monitor the queue for jobs.  Once it sees a job in that queue it will bring up a dialog box asking you where you want to fax the document to.

Hope this is enough to get you started in the right direction.

---

### Post by SirJ77 on 2007-09-27
Hmm, I'll see where that takes me... thanks for the tip.

edit:
Ok, what documentation did you find?  I found what appears to be a manpage off the efax site that makes a very vague reference to being able to do what you said, but doesn't say how.  Other searches haven't turned up anything except how to use an all-in-one fax printer to set a fax.  I just wanted to fax a resume some where, and thought this would a simple matter.  Fax software, say hi to ext fax modem, please send this document. :-k

Is there something else I should be trying instead of efax (keeping in mind that I'm running the xfce version)?

---

### Post by SirJ77 on 2007-09-28
I guess an edit does not bump it up the list so, bump.

---

