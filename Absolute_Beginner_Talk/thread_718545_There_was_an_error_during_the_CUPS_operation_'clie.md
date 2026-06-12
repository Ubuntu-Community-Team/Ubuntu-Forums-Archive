---
title: "There was an error during the CUPS operation: 'client-error-document-format-not-suppo"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Mark HUnter on 2008-03-08
Hello:

I am quite new to the Linux World, and I am having trouble getting my printer to work.  It is a Lexmark C500n colour printer.

The error I have been tryiing different things from the internet searches I have done.

When I try to print the test page (from System - Administration - Printing, I get the following error:

CUPS server error

There was an error during the CUPS operation: 'client-error-document-format-not-supported'.

I have done Google searches on this error and so far I cannot get anything to work.

Today I tried to do an install of a Driver that says it is for the C500N printer.  It is called foo2slx from site "http://foo2slx.rkkda.com/".  I went through the install and it appeared to be successful, except for this part (which I am not sure what it does:

sudo: gnome-cups-manager: command not found

When I try to print the test page, I still get the same error (There was an error during the CUPS operation: 'client-error-document-format-not-supported'.)

Anyone else experienced with this?

---

### Post by ellalan on 2008-03-09
You have to go to the Synaptic Package Manager and search for "gnome-cups-manager" and mark that for installation and click apply. It should be OK now.HTH.

---

