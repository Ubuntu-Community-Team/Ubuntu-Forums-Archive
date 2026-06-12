---
title: "OpenOffice Spreadsheet Issue"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by unknown user on 2007-12-18
**[COLOR="Navy"]I have received an email with Excel spreadsheet attached which I have opened up in OpenOffice all OK.  However, in Excel it opens up with a game in it, but when I open it in OpenOffice, there is just a big square with a cross in it.  I thought it was something to do with the macro security settings, but I can not find this in Open.  Can anyone help me with this one so that I can have the same functionality as Excel and play the game. Cheers,[/COLOR]**

---

### Post by Rhubarb on 2007-12-18
Well, it's probably best if you can't play games in your speadsheet application.
My guess is that the game in the speadsheet is a hidden visual basic macro (or maybe even a web page).

Why you shouldn't want to play games is speadsheets:
The game was put into a speadsheet so it can pass through many business' firewalls, so this "game" is targeted at mainly office workers.
This sounds to me like a great way to introduce a trojan onto many many office PCs.

Perhaps it's best to keep it as is, and don't attempt to play "games" in speadsheets + don't forward it on to other co-workers.

---

### Post by unknown user on 2007-12-19
It being my own machine I am not too bothered if it is a virus or anything like that as all my data is backed up and all I will do is install the OS again.  I am more worried about getting OpenOffice working for other needs in the future.  If they want to get you they will in the ned.

---

### Post by niteshifter on 2007-12-19
In Excel such added functionality, like a game or custom formulas / functions can be provided by macros written in Visual Basic for Applications (VBA), with ActiveX controls, .NET applications (VB, C++, C#, etc.) or a combination of these. Possibly the most common are "pure" VBA macros.

In OOo Calc added functionality is had in much the same way: OpenOffice Basic, Javascript, Python, and Beanshell can be used for macros. Java, C/C++ and almost any other language can be used to provide custom formulas and functions - even .NET (in the Windows version). OOo Basic is also possibly the most commonly encountered.

With either MS or OOo documents a very common approach is use the built-in macro language (VBA or OOo Basic) to link with "external" code (VB.NET, C++, Java, etc.)

The problem you're having (assuming the Excel sheet is using "pure" VBA) is that VBA and OpenOffice Basic are not the same. They are very similar - the bulk of the BASIC syntax is identical - but there are crucial differences in the syntax of how the document's internal environment and objects are accessed. When a Excel document is loaded into OOo the macros found are present but are never executed, as it will take some editing of the macro's code to have them perform properly.

Here's how to view them in OOo: Click "Tools" on the main menu, then click "Macros ....", then click on "Organize Macros", then click "OpenOffice Basic ..." (or whatever language is installed in OOo). That (the Basic one) will open OOo Basic's development environment. Your document's VBA macros (*if* that's what it's using) should be accessible there.

To access macro security: Click "Tools" on the main menu, then click "Options". This opens the OOo's Options dialog - the place where many features of OOo applications are controlled. In the left side pane of that dialog is a list, at the top of the list is the text "OpenOffice.org" with an indented list of items below it (if no such indent list is visible click on the small box to the left of OpenOffice.org). Click on "Security" in the indent list, the dialog will change, look for the button labeled "Macro Security" and click that to set up macro security.

But I stress, they won't work in OOo without some editing. How much depends upon the complexity of the macro's coding.

The forums of OpenOffice.org ( [http://www.oooforum.org/]("http://www.oooforum.org/") ) is a great place to ask for help on OOo Macros (and the underlying API) - nothing wrong with asking here of course, but the folks there live, eat and breathe the stuff.

The are converter apps / macros around that will convert VBA to OOo Basic, but I've never used them, so I can't speak to their utility.

---

### Post by unknown user on 2007-12-21
Hi there,
Thanks for the OOO forum link I have joind it and will see what they have got to say about this.  Hopefully, I will be able to sort it out and play the silly games and things that come around in excel format.

---

