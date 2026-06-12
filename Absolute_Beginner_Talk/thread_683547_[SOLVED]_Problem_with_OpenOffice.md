---
title: "[SOLVED] Problem with OpenOffice"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by A Pragmaticist on 2008-01-31
Hello,

I have a very weird problem with OpenOffice.  When I open some documents, they turn out fine.  But when I open up other ones, OpenOffice freezes and never fully loads the document.  What makes it really weird is that the document I have problem opening is the same extension as the other two I have no problems with: .doc.  When I booted into Vista, all three files were able to open up fine in MS Word.  All three files are simply plain text, no images.  I do not understand what it could be.  Any clues?

---

### Post by stoodleysnow on 2008-01-31
Did you use office 2007 to create any of the files, are there any tables or drawing objects of any kind, did you use columns, page breaks, headers or footers? :?:

---

### Post by A Pragmaticist on 2008-02-01
I did not create the files, they were sent to me and I suppose that they get around a bit, so it is probable that I will not be able to find out if any were made in Office 2007 or not; unless there is a way to find out that I do not know about?

It has endnotes (basically bibliographical references); no columns, tables, or all that other stuff.

Curiously, the document I have problems with works perfectly in Abiword, actually even better in Abiword than in MS Word.  Really, all three of the documents work in Abiword.  So I suppose that will work for me now, but if anyone knows what could be throwing off OpenOffice, I would appreciate finding out.

---

### Post by A Pragmaticist on 2008-02-01
I noticed that the problem document had footers, that for some reason were big and empty.  I do not know if the endnotes should have ended up in the footers or not.

---

### Post by Hagar Delest on 2008-02-01
If there is no sensitive data, can you upload it somewhere on a file sharing web site (like [mediafire.com](http://www.mediafire.com/))?
Have you tried to remove the footer and saving it under another name?

---

### Post by A Pragmaticist on 2008-02-01
Alright, I removed the footer, but I did not rename it.  Then when I tried to open it, I got this message:

"The filename ""Heidegger, Carnap and Quine at the Crossroads of Language" by Wanda Gregory.doc" indicates that this file is of type "Word document". The contents of the file indicate that the file is of type "RTF document". If you open this file, the file might present a security risk to your system.

Do not open the file unless you created the file yourself, or received the file from a trusted source. To open the file, rename the file to the correct extension for "RTF document", then open the file normally. Alternatively, use the Open With menu to choose a specific application for the file."

Could removing the footer have caused this, or does it seem likely that it came this way?  I am confused.

---

### Post by Hagar Delest on 2008-02-02
Have you saved it as .doc or .rtf? RTF is not so well supported by OOo IIRC.
If the format has changed by itself, that's rather weird indeed.

---

### Post by A Pragmaticist on 2008-02-02
Okay, so...

When I open the folder containing the document, it is listed as .doc

Then, when I select over it in the list, it turns into .rtf

Is this normal?

I then re-downloaded the file, took out the footer, renamed it, and now the new file that resulted does the same thing; i.e., is listed as .doc but turns into .rtf when I select it.  If I click again to open it, it gives me the same message as the first problem document.  If I move onto a new document after selecting it, it remains .rtf  But if I close out or move to another folder or directory and then come back, they both say .doc again.

As it turns out, if I right click and then open either with Abiword or with OpenOffice, they open normally now, as long as it is the file without the footer.  If it is the one with the footer, it only opens in Abiword.

Also, another document now that I did not have problems with does the same thing as the two that I created by removing the footer; i.e., if I double-click on it then it gives me the error window, but if I try to open it by right-clicking and selecting the program, it opens in both Abiword and OpenOffice.

The third document of the original three I downloaded is fine, no weird problems.

I am at a loss for the logic going on here.

---

### Post by A Pragmaticist on 2008-02-02
Saved as .doc

---

### Post by Hagar Delest on 2008-02-02
If you remove the file extension, what's the Nautilus opinion about it? Can you upload somewhere a sample file?

---

### Post by A Pragmaticist on 2008-02-02
Okay, so this is what happened when I fiddled with the file extensions:

When I removed the extension from the file -- the one with the footer removed from the original --, it now just interprets as rtf document, and there is no specific extension on the file name.  It also opens in Abiword and OpenOffice with no problems, although OpenOffice had to recover the file first.  There was a weird problem before in which the bibliography was cut off, but now I get all of it in OpenOffice.  Unfortunately, Abiword is still cutting it off; they had both been cutting it before, but at different parts.

When I removed the extension from the file -- the original prior to removal of the footer -- it still only opens in Abiword, not in OpenOffice, and Nautilus interprets the file as "OLE2 compound document storage".

I'll try uploading the original, be getting back to you on that.

---

### Post by A Pragmaticist on 2008-02-02
On MediaFire:

Original document with file extension: [http://www.mediafire.com/?4yyrm5vuc3g](http://www.mediafire.com/?4yyrm5vuc3g)

Original document with file extension removed: [http://www.mediafire.com/?4yyrm5vuc3g](http://www.mediafire.com/?4yyrm5vuc3g)

Edited document with file extension: would not upload.  I got this message from MediaFire: "Oops! No files were found. This error has been forwarded to MediaFire's development team.  There were no files found when your upload began. Please insure that there are no applications running that may be blocking your upload."  However, that same file I can open in both Abiword and OpenOffice, so I am not sure what is going on; then again, if I attempt to open the file by double-clicking, I get the error I mentioned before about a conflict between file name and content.

Edited document with file extension removed: [http://www.mediafire.com/?byltxdihvmy](http://www.mediafire.com/?byltxdihvmy)

I hope this is helpful.

---

### Post by Hagar Delest on 2008-02-02
You've posted twice the second file it seems. So we don't have the original.

I remember such an issue now. In fact, when picking a format in the drop-down list, OOo would save with the n following format in the list (don't recall the value of n). Try to save in another format and see if you can confirm. For example if you select the  entry immediately after .doc (beware, there are several entries for .doc), then, it should save in the format immediately after the .rtf entry in that same drop-down list.

If so, try to rename your OOo user profile (~/.openoffice.org2). I'm not sure it was the fix but it's worth trying.

---

### Post by Joe Dinmore on 2008-02-02
It seems to me, at least possible  that the *original* file was an rtf file saved with a .doc extension.

---

### Post by A Pragmaticist on 2008-02-03
> **Hagar de l'Est said:**
> You've posted twice the second file it seems. So we don't have the original.

I remember such an issue now. In fact, when picking a format in the drop-down list, OOo would save with the n following format in the list (don't recall the value of n). Try to save in another format and see if you can confirm. For example if you select the  entry immediately after .doc (beware, there are several entries for .doc), then, it should save in the format immediately after the .rtf entry in that same drop-down list.

If so, try to rename your OOo user profile (~/.openoffice.org2). I'm not sure it was the fix but it's worth trying.

Well, I saved the edited file without the extension, as rtf.  I was warned that some content might be lost, and then I proceeded.  A new file appeared with the same name, but the extension ".rtf" added, and the file size went from 58.3 KB to 72.1 KB, seemingly with no change in the content of the file.  RTF was the format I could save in right after the three possible .doc formats, so it did not save the "n" following format.

---

### Post by A Pragmaticist on 2008-02-03
Yeah, as I just found out, when I attempt to upload the original with the file extension still added, it comes up with exactly the same URL as the original without the file extension.  I should have noticed that before, I must have not realized I posted the same URL for both.  I am not sure what this means, that two of them are recognized as the same by mediafire and another is not even seen as a file at all; pretty bizarre.

---

### Post by A Pragmaticist on 2008-02-03
> **Joe Dinmore said:**
> It seems to me, at least possible  that the *original* file was an rtf file saved with a .doc extension.

That could very well be.  Do you know of a reason why that would cause problems opening it in OpenOffice but not in Abiword?  Or why it might cause part of the paper to be cut out in Abiword?

---

### Post by Hagar Delest on 2008-02-03
RTF is not so documented IIRC or there are so many versions of it that it's rather difficult to have a good import/export filter. This is why using open formats like ODF (.odt, .ods, .odp, ...) is very important. For the user. It insures that data will be accessible anytime in the future.

---

### Post by A Pragmaticist on 2008-02-03
So...I should just change the format before opening a file in OpenOffice?

---

### Post by Hagar Delest on 2008-02-04
Not before. Changing the extension manually has no impact on the file. Open it and Save As .odt. But if the document needs to be edited by someone who can't use OOo, then, you'll need to keep .rtf or .doc formats.

---

### Post by A Pragmaticist on 2008-02-04
Alright, just to make sure this is right: so basically I need to use Abiword to open the file originally (since my problem in the first place is that the problem document would not even open in OpenOffice at all), change the format to one accepted by OpenOffice, then open it in OpenOffice and change it to the open format.  Then I can change it to .rtf or .doc for anyone who does not have OpenOffice.  Is this the procedure I should follow henceforth?

---

### Post by Hagar Delest on 2008-02-04
Basically, use the native ODF format as often as you can. Export the file in another format only at the end.

One last question: it seems that the file has been wrongly named .doc by the site where you've downloaded it. If you change manually the extension to .rtf (in this case, you can), does it also freeze OOo?

Using Abiword is just a workaround if you can't open the file directly in OOo. Note that sometimes, just saving again in the same format (no need to perform any change at all) can fix it, it's also worth trying (instead of saving in a different format, with the risk of formatting loss).

---

### Post by A Pragmaticist on 2008-02-05
> **Hagar de l'Est said:**
> Basically, use the native ODF format as often as you can. Export the file in another format only at the end.

One last question: it seems that the file has been wrongly named .doc by the site where you've downloaded it. If you change manually the extension to .rtf (in this case, you can), does it also freeze OOo?

Using Abiword is just a workaround if you can't open the file directly in OOo. Note that sometimes, just saving again in the same format (no need to perform any change at all) can fix it, it's also worth trying (instead of saving in a different format, with the risk of formatting loss).

I changed it manually and yes, it also freezes OOo.

---

### Post by A Pragmaticist on 2008-02-05
And now I just saved it as .doc in Abiword, and it opens in OOo without a problem.

---

