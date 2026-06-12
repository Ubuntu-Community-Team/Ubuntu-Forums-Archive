---
title: "[SOLVED] how do I re-edit text in Gimp"
date: 2008-09-10
forum: Art &amp; Design
---

### Post by charonred on 2008-09-10
this is really infuriating me; I have some images with layers containing text - I want to edit some of the existing text but for the life of me I can't figure out how.

I select the layer, then click on it with the text tool, but all it does is open a fresh text box, not one with existing text in it.

I was never a very experienced user of photoshop, but I could do some basic things and that was all I needed. However I can't seem to make some of these simple things happen in Gimp; it's certainly not making the change from XP to Ubuntu easy.

Is there a simple guide to using Gimp cause its 'Help' pages are not!

---

### Post by Pasto on 2008-09-10
On the Layers window, right button on the text layer, choose "Text Tool" and it opens the initial dialog box to type text, where you can change it.

There must be an easier way though.

---

### Post by Pasto on 2008-09-10
Mmm just tested what you said and it works for me.

Selecting the text layer, then using the text tool and clicking on the text opens the same dialog to edit the text. Are you 100% positive that you have the right layer selected? If I have a different layer selected a new dialog will popup as you said.

---

### Post by charonred on 2008-09-10
thanks for the super fast reply.

As far as I can tell I have selected the correct layer; but if I right click on it in the layer window, there is no option to choose 'text tool'

this is Gimp 2.4.6 
does that make any difference, do I need to re-install it?

---

### Post by charonred on 2008-09-10
*bump* - I still can't get Gimp to re-edit text.

---

### Post by Half-Left on 2008-09-10
Thats because you may have applied a filter to it, it's abit like Photoshop how you rasterize the layer.

You have to click the text tool and then click the text on the canvas(not on the layers tab), then it will ask if you want to edit the text, this removes any filters you have applied.

Yes I know it's not as flexible as Photoshop but you'll find having to get your text right first is the best way to work with GIMP. This applies to effects as well, unlike Photoshop where you can edit and change them as you go.

You'll find extra plugins like layer effects for Photoshop in the Ubuntu repos, but they are not as flexible, i.e they dont show in reatime how the effect will be on your text, unlike Photoshop does. It's the down side of GIMP but like me you can adjust your way of working to get around it, I have.

---

### Post by munkyeetr on 2008-09-10
> **Pasto said:**
> On the Layers window, right button on the text layer, choose "Text Tool" and it opens the initial dialog box to type text, where you can change it.

This also works for me, no problem.

One thing though, which may be the culprit, if you have rotated the text you can no longer edit it ASAIK as shown above. There may be other instances where you can no longer edit text, but rotate is the only one I have come across personally.

---

### Post by Half-Left on 2008-09-10
> **munkyeetr said:**
> This also works for me, no problem.

One thing though, which may be the culprit, if you have rotated the text you can no longer edit it ASAIK as shown above. There may be other instances where you can no longer edit text, but rotate is the only one I have come across personally.

You can edit your text by using the technic I just post, but it resets your text.

---

### Post by charonred on 2008-09-10
thanks all.

I haven't applied any filters.

Say I create a new layer and add an image to it, then I add another layer with some text on it, then save and exit.

I re-open it, select the layer, click text tool and then click on actual text; it opens a new text box with no existing text, which means I have to re-type the text again, instead of just altering a word or two, then delete the existing layer - not very efficient.

---

### Post by donec on 2008-09-10
I may be wrong but5 if you anchor the text or merg the text to another layer then you can not edit the text you just have to replace it.

---

### Post by Half-Left on 2008-09-10
> **charonred said:**
> thanks all.

I haven't applied any filters.

Say I create a new layer and add an image to it, then I add another layer with some text on it, then save and exit.

I re-open it, select the layer, click text tool and then click on actual text; it opens a new text box with no existing text, which means I have to re-type the text again, instead of just altering a word or two, then delete the existing layer - not very efficient.

Not sure what your doing wrong, if you save as a .xcf gimp format, when you open it again the text layer will be preserved.

---

### Post by Half-Left on 2008-09-10
> **donec said:**
> I may be wrong but5 if you anchor the text or merg the text to another layer then you can not edit the text you just have to replace it.

Correct your not wrong.

---

### Post by charonred on 2008-09-10
Thanks Half-Left
> Not sure what your doing wrong, if you save as a .xcf gimp format, when you open it again the text layer will be preserved.

I've now figured it out; I feel somewhere between stupid, and expecting too much out of Gimp.
 
I was in the habit of saving project files as .psd and finished ones as .jpg for printing (CDs etc) - I just expected to be able to re-edit my .psd files.

I opened my blank-dvd.psd file and this time saved as blank-dvd.xcf then added some layers, saved and exited. 

When I re-opened the blank-dvd.xcf file, I was able to re-edit the text layers as described in posts - DOH ! DOH ! DOH !

---

### Post by munkyeetr on 2008-09-10
> **Half-Left said:**
> You can edit your text by using the technic I just post, but it resets your text.

I missed that post of yours! Thank you. That will sure save me time in the future.

---

### Post by Half-Left on 2008-09-11
> **charonred said:**
> Thanks Half-Left


I've now figured it out; I feel somewhere between stupid, and expecting too much out of Gimp.
 
I was in the habit of saving project files as .psd and finished ones as .jpg for printing (CDs etc) - I just expected to be able to re-edit my .psd files.

I opened my blank-dvd.psd file and this time saved as blank-dvd.xcf then added some layers, saved and exited. 

When I re-opened the blank-dvd.xcf file, I was able to re-edit the text layers as described in posts - DOH ! DOH ! DOH !

No problem.

Just remember with GIMP you have to get your text right first before applying effects, with Photoshop can can adjust the layer effects on the fly, with GIMP your limited how to change them.

Once you get to work this way you'll find you can follow just about any Photoshop tutorial to achieve the same effect.

Check out my vid, [http://www.youtube.com/watch?v=HKDX6e8pgu4](http://www.youtube.com/watch?v=HKDX6e8pgu4)

---

### Post by blogote on 2009-10-19
Registered here to see the attachment .. doesn't help :confused:

I have a PSD whose text needs to be needed.. very much frustrating for me! Any help?

Using gimp to edit it.. but unable to do so.

---

### Post by Exodist on 2009-10-19
> **blogote said:**
> Registered here to see the attachment .. doesn't help :confused:

I have a PSD whose text needs to be needed.. very much frustrating for me! Any help?

Using gimp to edit it.. but unable to do so.

Question: 
Is the document still have its layers with the TEXT in its own layer?
If YES: Then select that layer from the layer dialog box, then with the text tool click on one of the letters of the word you wish to edit. 
If NO: You cant.

---

### Post by webcomm on 2012-03-29
I did what Exodus suggested but still can't edit text.  I opened a PSD created in photoshop and saved as an XCF.  I am now trying to edit text.  I select the layer in the layers dialog.  I click the text tool.  I can see dotted lines around the text so I know it's selected.  But if I click on it with the text tool, I see the "Gimp text editor" popup.  But there is no text in it.  I am zooming way in so that I know for sure I am actually clicking on the letters themselves.  If I type text in the Gimp text editor, it just creates a new layer which is *also* not editable after the editor is closed.

---

### Post by overdrank on 2012-03-29
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

