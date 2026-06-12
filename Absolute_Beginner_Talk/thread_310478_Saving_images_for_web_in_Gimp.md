---
title: "Saving images for web in Gimp"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2006-12-01
Having resized an image to include with an email, I've looked to save it for web as I did in Photoshop but failed to find anything like this feature.  Is there something similar in The Gimp which allows you to save an image for the web?

---

### Post by rsambuca on 2006-12-01
I'm not quite sure what you mean when you say "save an image for the web".  Most images on websites are in jpeg format, and you can easily save it in that format with Gimp when saving.  When saving, go to File - Save As - Save File type by Extension (select jpeg).

Note:  if you are doing a lot of editing to a photo over numerous sessions, save it in the native Gimp format until you are done, and then save it in jpeg only after you are finished.  Every time you save a jpeg image you will lose quality due to compression artifacts.

---

### Post by charlesw on 2006-12-02
a.v.l, your referring to photoshops save for webcommand sadly and to my dismay the gimp simly dosent have a save for web plugin it never has and thats one of the main reasons i still have a windows computer the open source tools work just fine but theres just certain features there lacking that some of us need or cant work around easily. if you happen to have photoshop 7 you can run it in wine just fine for the most part though. :)

---

### Post by CarpKing on 2006-12-02
What does the "Save for Web" command do, exactly?  If we knew that, we could probably describe a way to do something similar in GIMP.  Or is it just one of those magic Photoshop things that automatically makes everything better in some indescribable way?

---

### Post by charlesw on 2006-12-02
save for web is basically a plugin/program  in photoshop its under File if you click File>Save for Web it opens a new window that allows you to edit the file size and filetype extension of your file it also gives you a 2up and 4up veiw.

1 pane, 2 panes original and optimized veiw or 4 panes original, compressed, compressed more, Really compressed and such but it also alows you to set interlacing options,blur and other settings.

the neat thing though is it lets you preview your changes in real time so you can see what it would look like compressed as a 32 bit gif without dithering or a 128 bit gif with dithering.

you can set the width and height you want the output to be and also set a desired file size and once you create a "profile setting" for lack of a better explanation you can save that setting you created and use it later on other images. 

It also alows you to choose how many colors you want to use, I use alot of software but i havent found anything for linux that equals the Save for Web feature in photoshop for ease of use features and consistency of results. If someone were to program a gimp plugin that had similar features with the same ease of use and consistency of file size and the results looked good everytime im quite sure it would be hugley popular i hate the fact that i cant make a 200x200 image in gimp and easly save it how i want it just to open it with photoshop and run the save for web tool on it. and yeah i know if you export the jpg you get a quality slider..  but its just not anywhere near the same. preview is a good thing.

chuck.

---

### Post by IYY on 2006-12-02
There is no such specific feature, but you can certainly do the same thing. Just change the mode of the image to indexed mode (Image > Mode > Indexed) and select your palette. I think all of the options from the Save For Web feature are available in that window. Then, just save the image as GIF and you're done.

---

### Post by TerryHowe on 2006-12-02
I don't think "save for web" is all that important anymore because browsers today don't have a limited color display capability.  Used to be more important when you wanted to save with a "web safe color pallet".

---

### Post by charlesw on 2006-12-02
how do i tell gimp i want my 800x600 image not to be pixellated as hell and only be 20kb and no more.. how can i save that output setting to use it for 400 pics without learning a scripting language and writing a plugin ? .. just examples to real world problems i have using gimp. dont get me wrong I think the gimp rocks for most of the stuff i do with it tiled backgrounds for a webpage is a no brainer in gimp and one of the things i find really really usefull .. thats what i mean by ease of use.

like 2 clicks and bam tileable bg image if there was a way to optimize output settings just as easily i think that would be awesome but it just the preivew modes avalible and the way you have acess to the options could be more intuitive.

---

