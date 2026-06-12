---
title: "saving web pages using Firefox"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by samsaw on 2007-05-13
I'm new to Ubuntu/Firefox; the system I'm used to is Mac OSX/Safari. With Safari, if I want to save a web page I do File -> Save As -> Web Archive, and the page is saved (seemingly) in one piece. With Firefox an associated folder is generated; and if I want to later delete the page, I have to delete the folder separately. Is there any way to save the folder elsewhere from where the page is being saved? And/or to somehow connect them so when one is deleted or moved, the other follows with it?

Sorry if I'm missing something very obvious here. I'm still getting used to do things a little differently.

---

### Post by raylu on 2007-05-13
I'm not quite sure how Safari works, but it isn't possible to save a webpage in one piece. Unless the webpage is just a piece of text, it contains references to images and such. Those have to be saved somewhere. Unless Mac OSX/Safari has its own format for saving all of this into one file, I don't see how they could do it.

---

### Post by annda on 2007-05-13
EDIT: sorry, i didn't read your post carefully till the end.

safari, just like IE, seems to automatically link the files. not so for FF. i suppose it's because FF is an external application and safari/ie are system browsers, benefiting close OS integration.

---

### Post by samsaw on 2007-05-13
> **raylu said:**
> I'm not quite sure how Safari works, but it isn't possible to save a webpage in one piece. Unless the webpage is just a piece of text, it contains references to images and such. Those have to be saved somewhere. Unless Mac OSX/Safari has its own format for saving all of this into one file, I don't see how they could do it.

It could well be the case that it just *looks* like one piece. What happens is, I save the page and an icon appears, for example, on the desktop (where I usually save to before filing it away somewhere). That's it. The page then opens perfectly if I click on it. I've never seen an associated folder and have no idea where such folders go if indeed they're generated. 

Basically, I'm unused to dealing with two 'pieces'.

---

### Post by samsaw on 2007-05-13
> **annda said:**
> ctrl+s

make sure the option "webpage, complete" is selected (it's the default setting, but who knows...)

That's what I do.

---

### Post by annda on 2007-05-13
my bad, the post was irrelevant. see my apologies above.

---

### Post by samsaw on 2007-05-13
> **annda said:**
> EDIT: sorry, i didn't read your post carefully till the end.

safari, just like IE, seems to automatically link the files. not so for FF. i suppose it's because FF is an external application and safari/ie are system browsers, benefiting close OS integration.

That makes sense, thanks.

---

### Post by raylu on 2007-05-14
> **annda said:**
> EDIT: sorry, i didn't read your post carefully till the end.

safari, just like IE, seems to automatically link the files. not so for FF. i suppose it's because FF is an external application and safari/ie are system browsers, benefiting close OS integration.
Um...that doesn't make sense. Saving webpages isn't an OS-level thing...

It's possible that Safari links to the files on the web instead of downloading them. You can check if you open up the file and look inside; pastebin it if you're not sure.

---

### Post by esoterica on 2007-05-14
There isn't a save as web archive option that I've ever seen for Firefox, even when running Firefox under Windows like you can do with IE.

Here's more, Firefox out of the box will also not save all the content layout information either, so if the page you are saving is a modern page created using XHTML and CSS for the layout, then your saved page isn't going to contain the specific layout information when viewed on your local computer offline.

There is however a Firefox add on called "Save Complete" that you will want to have for this reason...

[https://addons.mozilla.org/en-US/firefox/addon/4723](https://addons.mozilla.org/en-US/firefox/addon/4723)

This will save the CSS file in addition to the images and stuff used in the web page.

A work around to what your wanting to do here and have everything saved as a single file with layout and images would be to use Open Office. You can copy the web page, then paste it into a word document and save it that way as a .doc file. You'll be able to see the entire page as it was when you copied it, but just in the Open Office program instead of your web browser, links and everything will still work in the doc file.

---

