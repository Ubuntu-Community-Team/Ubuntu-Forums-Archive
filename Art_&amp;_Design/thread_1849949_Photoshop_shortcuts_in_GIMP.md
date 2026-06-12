---
title: "Photoshop shortcuts in GIMP"
date: 2011-09-25
forum: Art &amp; Design
---

### Post by jampe on 2011-09-25
As I thought to myself that the current ones (appropriated from Photoshop 6) were a bit outdated, I took the liberty of redoing them to reflect more recent Photoshop releases.

To install (close down GIMP first):
1. cd ~/.gimp-2.*/
2. mv menurc menurc-bak
3. gedit menurc
4. paste this code
5. save

I organised them alphabetically, making it a bit easier to comprehend. If you guys decide to use them, and you run into some shortcuts that I missed, it would be neat if you would submit them to this thread.

```

; Photoshop keybindings for the GIMP

; CONTEXT
(gtk_accel_path "<Actions>/context/context-brush-select-last" "greater")
(gtk_accel_path "<Actions>/context/context-brush-select-first" "less")
(gtk_accel_path "<Actions>/context/context-brush-hardness-decrease-skip" "braceleft")
(gtk_accel_path "<Actions>/context/context-brush-hardness-increase-skip" "braceright")
(gtk_accel_path "<Actions>/context/context-brush-radius-decrease-skip" "bracketleft")
(gtk_accel_path "<Actions>/context/context-brush-radius-increase-skip" "bracketright")
(gtk_accel_path "<Actions>/context/context-brush-select-previous" "comma")
(gtk_accel_path "<Actions>/context/context-brush-select-next" "period")

; DIALOGS
(gtk_accel_path "<Actions>/dialogs/dialogs-layers" "F7")
(gtk_accel_path "<Actions>/dialogs/dialogs-brushes" "")
(gtk_accel_path "<Actions>/dialogs/dialogs-channels" "<Shift>F7")
(gtk_accel_path "<Actions>/dialogs/dialogs-preferences" "<Control>k")
(gtk_accel_path "<Actions>/dialogs/dialogs-gradients" "<Shift><Control>g")
(gtk_accel_path "<Actions>/dialogs/dialogs-colors" "F6")
(gtk_accel_path "<Actions>/dialogs/dialogs-tool-options" "F5")
(gtk_accel_path "<Actions>/dialogs/dialogs-undo-history" "<Shift>F9")
(gtk_accel_path "<Actions>/dialogs/dialogs-vectors" "F9")
(gtk_accel_path "<Actions>/dialogs/dialogs-document-history" "<Shift><Control>h")
(gtk_accel_path "<Actions>/dialogs/dialogs-palettes" "<Shift><Control>l")

; DRAWABLE
(gtk_accel_path "<Actions>/drawable/drawable-desaturate" "<Shift><Control>u")
(gtk_accel_path "<Actions>/drawable/drawable-invert" "<Control>i")

; EDIT
(gtk_accel_path "<Actions>/edit/edit-named-copy" "")
(gtk_accel_path "<Actions>/edit/edit-named-paste" "")
(gtk_accel_path "<Actions>/edit/edit-paste-into" "<Shift><Control>v")
(gtk_accel_path "<Actions>/edit/edit-fill-fg" "<Alt>BackSpace")
(gtk_accel_path "<Actions>/edit/edit-clear" "")
(gtk_accel_path "<Actions>/edit/edit-redo" "<Shift><Control>z")
(gtk_accel_path "<Actions>/edit/edit-fill-bg" "<Control>BackSpace")
(gtk_accel_path "<Actions>/edit/edit-fill-pattern" "")
(gtk_accel_path "<Actions>/edit/edit-named-cut" "")

; FILE
(gtk_accel_path "<Actions>/file/file-save-a-copy" "<Control><Alt>s")
(gtk_accel_path "<Actions>/file/file-open-recent-10" "")
(gtk_accel_path "<Actions>/file/file-revert" "F12")

; IMAGE
(gtk_accel_path "<Actions>/image/image-scale" "<Control><Alt>i")
(gtk_accel_path "<Actions>/image/image-resize" "<Control><Alt>c")
(gtk_accel_path "<Actions>/image/image-merge-layers" "<Shift><Control>e")
(gtk_accel_path "<Actions>/image/image-duplicate" "")
(gtk_accel_path "<Actions>/image/image-rotate-180" "8")
(gtk_accel_path "<Actions>/image/image-flatten" "<Shift>i")
(gtk_accel_path "<Actions>/image/image-rotate-270" "7")
(gtk_accel_path "<Actions>/image/image-convert-indexed" "backslash")
(gtk_accel_path "<Actions>/image/image-rotate-90" "9")

; LAYERS
(gtk_accel_path "<Actions>/layers/layers-resize-to-image" "<Alt>y")
(gtk_accel_path "<Actions>/layers/layers-alpha-selection-replace" "<Alt>a")
(gtk_accel_path "<Actions>/layers/layers-duplicate" "<Control>j")
(gtk_accel_path "<Actions>/layers/layers-preserve-transparency" "slash")
(gtk_accel_path "<Actions>/layers/layers-new" "<Shift><Control>n")
(gtk_accel_path "<Actions>/layers/layers-select-bottom" "<Alt>braceleft")
(gtk_accel_path "<Actions>/layers/layers-mode-previous" "underscore")
(gtk_accel_path "<Actions>/layers/layers-mode-next" "plus")
(gtk_accel_path "<Actions>/layers/layers-select-previous" "<Alt>bracketright")
(gtk_accel_path "<Actions>/layers/layers-lower-to-bottom" "<Control>braceleft")
(gtk_accel_path "<Actions>/layers/layers-mask-add" "<Alt>o")
(gtk_accel_path "<Actions>/layers/layers-lower" "<Control>bracketleft")
(gtk_accel_path "<Actions>/layers/layers-raise-to-top" "<Control>braceright")
(gtk_accel_path "<Actions>/layers/layers-merge-down" "<Control>e")
(gtk_accel_path "<Actions>/layers/layers-raise" "<Control>bracketright")
(gtk_accel_path "<Actions>/layers/layers-anchor" "<Alt>h")
(gtk_accel_path "<Actions>/layers/layers-select-top" "<Alt>braceright")
(gtk_accel_path "<Actions>/layers/layers-select-next" "<Alt>bracketleft")

; PLUG-IN
(gtk_accel_path "<Actions>/plug-in/tiny_fu_refresh" "<Shift><Control><Alt>t")
(gtk_accel_path "<Actions>/plug-in/plug_in_c_astretch" "<Shift><Control><Alt>l")
(gtk_accel_path "<Actions>/plug-in/plug_in_bump_map" "<Shift><Control>m")
(gtk_accel_path "<Actions>/plug-in/plug_in_iwarp" "<Shift><Control>x")
(gtk_accel_path "<Actions>/plug-in/plug_in_gauss" "<Shift><Control>b")
(gtk_accel_path "<Actions>/plug-in/file_print_gimp" "<Control>p")
(gtk_accel_path "<Actions>/plug-in/script_fu_refresh" "<Shift><Control><Alt>r")
(gtk_accel_path "<Actions>/plug-in/plug_in_colortoalpha" "<Shift><Control>a")

; QMASK
(gtk_accel_path "<Actions>/qmask/qmask-toggle" "q")

; SELECT
(gtk_accel_path "<Actions>/select/select-feather" "<Shift><Control>d")
(gtk_accel_path "<Actions>/select/select-none" "<Control>d")
(gtk_accel_path "<Actions>/select/select-float" "")
(gtk_accel_path "<Actions>/select/select-invert" "<Shift><Control>i")

; TOOLS
(gtk_accel_path "<Actions>/tools/tools-dodge-burn" "o")
(gtk_accel_path "<Actions>/tools/tools-clone" "s")
(gtk_accel_path "<Actions>/tools/tools-ellipse-select" "<Shift>m")
(gtk_accel_path "<Actions>/tools/tools-vector" "p")
(gtk_accel_path "<Actions>/tools/tools-scale" "<Control>t")
(gtk_accel_path "<Actions>/tools/tools-paintbrush" "b")
(gtk_accel_path "<Actions>/tools/tools-airbrush" "j")
(gtk_accel_path "<Actions>/tools/tools-blend" "g")
(gtk_accel_path "<Actions>/tools/tools-free-select" "l")
(gtk_accel_path "<Actions>/tools/tools-eraser" "e")
(gtk_accel_path "<Actions>/tools/tools-color-balance" "<Control>b")
(gtk_accel_path "<Actions>/tools/tools-by-color-select" "<Shift><Control>c")
(gtk_accel_path "<Actions>/tools/tools-levels" "<Control>l")
(gtk_accel_path "<Actions>/tools/tools-bucket-fill" "<Shift>g")
(gtk_accel_path "<Actions>/tools/tools-convolve" "r")
(gtk_accel_path "<Actions>/tools/tools-magnify" "z")
(gtk_accel_path "<Actions>/tools/tools-move" "v")
(gtk_accel_path "<Actions>/tools/tools-curves" "<Control>m")
(gtk_accel_path "<Actions>/tools/tools-measure" "u")
(gtk_accel_path "<Actions>/tools/tools-crop" "c")
(gtk_accel_path "<Actions>/tools/tools-iscissors" "")
(gtk_accel_path "<Actions>/tools/tools-rotate" "")
(gtk_accel_path "<Actions>/tools/tools-hue-saturation" "<Control>u")
(gtk_accel_path "<Actions>/tools/tools-rect-select" "m")
(gtk_accel_path "<Actions>/tools/tools-flip" "f")
(gtk_accel_path "<Actions>/tools/tools-smudge" "")
(gtk_accel_path "<Actions>/tools/tools-fuzzy-select" "w")
(gtk_accel_path "<Actions>/tools/tools-color-picker" "i")

; VIEW
(gtk_accel_path "<Actions>/view/view-show-selection" "<Control>h")
(gtk_accel_path "<Actions>/view/view-zoom-in" "<Control>equal")
(gtk_accel_path "<Actions>/view/view-show-grid" "<Control><Alt>apostrophe")
(gtk_accel_path "<Actions>/view/view-info-window" "F8")
(gtk_accel_path "<Actions>/view/view-zoom-out" "<Control>minus")
(gtk_accel_path "<Actions>/view/view-zoom-1-1" "<Control><Alt>0")
(gtk_accel_path "<Actions>/view/view-zoom-fit-in" "")
(gtk_accel_path "<Actions>/view/view-navigation-window" "")
(gtk_accel_path "<Actions>/view/view-show-rulers" "<Control>r")
(gtk_accel_path "<Actions>/view/view-scroll-page-down" "Page_Down")
(gtk_accel_path "<Actions>/view/view-show-menubar" "<Shift>f")
(gtk_accel_path "<Actions>/view/view-snap-to-guides" "<Control>semicolon")
(gtk_accel_path "<Actions>/view/view-show-guides" "<Control>apostrophe")
(gtk_accel_path "<Actions>/view/view-zoom-fit-to" "<Control>0")
(gtk_accel_path "<Actions>/view/view-scroll-page-up" "Page_Up")
(gtk_accel_path "<Actions>/view/view-scroll-page-right" "<Control>Page_Down")
(gtk_accel_path "<Actions>/view/view-scroll-page-left" "<Control>Page_Up")
(gtk_accel_path "<Actions>/view/view-shrink-wrap" "")

```

---

### Post by prokoudine on 2011-09-30
> **jampe said:**
> As I thought to myself that the current ones (appropriated from Photoshop 6) were a bit outdated

They are not. I personally updated them to match CS4 a year ago or so :) We ditched the file later in 2.7 dev cycle though :)

---

### Post by jampe on 2011-10-05
> **prokoudine said:**
> They are not. I personally updated them to match CS4 a year ago or so :) We ditched the file later in 2.7 dev cycle though :)

So you personally updated them, but them threw them away? How does that help anyone? :D

---

### Post by ofnuts on 2011-10-05
> **jampe said:**
> So you personally updated them, but them threw them away? How does that help anyone? :DIt helps make them understand that Gimp Is Not Photoshop... :D

---

### Post by jampe on 2011-10-11
> **ofnuts said:**
> It helps make them understand that Gimp Is Not Photoshop... :D

I understand the sentiment, but one of the main points of software like this is that people get to choose for themselves. If you want to, you should be able to use Photoshop shortcuts, even MS Paint shortcuts if you bloody well please :D

---

### Post by graphius on 2011-10-17
I am sorry, I have to rant.
Throwing away the key bindings because you want to prove to people that Gimp is not Photoshop is stupid.
Photoshop is THE premier image editing software, for good or ill. There are more tutorials, books, college courses, etc for PS than for Gimp. Keeping the same keyboard shortcuts would add to the usefulness of Gimp.
(I agree that they are largely irrelevant. I used to use both Photoshop and Corel Paint, and those both had opposite shortcuts.) but to throw out the file....WTF?
end rant
Gimp is a great program. Keyboard shortcuts are the least of its problems. I am looking forward to GEGL. I also wish Gimp had adjustment layers, and handled window focus better, but for a free program, in all senses of the word, it is great... but it is not Photoshop....

---

### Post by ofnuts on 2011-10-18
> **graphius said:**
> I am sorry, I have to rant.
Throwing away the key bindings because you want to prove to people that Gimp is not Photoshop is stupid.
Photoshop is THE premier image editing software, for good or ill. There are more tutorials, books, college courses, etc for PS than for Gimp. Keeping the same keyboard shortcuts would add to the usefulness of Gimp.
(I agree that they are largely irrelevant. I used to use both Photoshop and Corel Paint, and those both had opposite shortcuts.) but to throw out the file....WTF?
end rant
Gimp is a great program. Keyboard shortcuts are the least of its problems. I am looking forward to GEGL. I also wish Gimp had adjustment layers, and handled window focus better, but for a free program, in all senses of the word, it is great... but it is not Photoshop....

[LIST=1]
[*]note the smiley
[*] keeping the same shortcuts is OK if they do ***[SIZE=4]exactly[/SIZE]*** the same thing (for instance, when creating a new layer, fill it with white and not make it transparent (bad example likely, but I don't know PS)). But I've yet to see a tutorial or course describing the action in terms of shortcuts... it's already bad enough when the only talk about menu items.
[*]in a parallel world, people using both MS-Office and {Open,Libre}Office live pretty well with seemingly opposite shortcuts at places.
[/LIST]

---

### Post by graphius on 2011-10-18
@ofnuts
Yes I got a little carried away. The problem is I really want to like and use Gimp. In fact I tried to use it exclusively for a couple of years. I strongly believe in the open source concept.
*jampe*, out of the kindness of his/her heart, made a photoshop compatible shortcut file.
*prokoudine* basically said that it was already done, but then thrown out. A bit of a slap in the face for *jampe*
you (*ofnuts*), IMHO, added insult to injury by saying, in effect, "We don't need no stinkin' Photoshop here". Yes you had smilies, but it still ignores the work that *jampe* did.

To put this thread back on track, I think these shortcuts are a great idea. No they will not be exactly the same, but they will still entice people to upgrade to the Gimp from say Adobe Elements.

---

### Post by NewAmercnClasic on 2011-10-19
I'd use gimp more if I could use photoshop shortcuts easier, usually I just pull up photoshop through wine.

---

### Post by prokoudine on 2011-10-22
> **graphius said:**
> I am sorry, I have to rant.
Throwing away the key bindings because you want to prove to people that Gimp is not Photoshop is stupid.

I love you too :)

> **graphius said:**
> Photoshop is THE premier image editing software, for good or ill. There are more tutorials, books, college courses, etc for PS than for Gimp. Keeping the same keyboard shortcuts would add to the usefulness of Gimp.

Exactly how would it do that?

> **graphius said:**
> (I agree that they are largely irrelevant. I used to use both Photoshop and Corel Paint, and those both had opposite shortcuts.) but to throw out the file....WTF?

Let's some it up. You think that Photoshop shortcuts are largely irrelevant, but nevertheless add usefulness. I have to say I'm genuinely puzzled :)

Photoshop and GIMP are two different mindsets. People who want Photoshop shortcuts in GIMP get a crippled crossbreed. It's fine for someone to maintain this outside of mainstream GIMP project, but it doesn't belong to mainstream GIMP.

---

### Post by graphius on 2011-10-22
@prokoudine
My rant was about taking away choice.
Way more serious graphic artists use Photoshop than Gimp. 
Making it easier for these same artists to switch between Gimp and Photoshop could only be good for Gimp.
The problem I see is devs who say it has to be their way. I am more than willing to admit that devs, especially Gimp developers, have some great ideas, but to throw away an OPTIONAL setting, because it is not "The Gimp Way" seems silly.
For casual users, the shortcuts are a minor point, but to stretch the assumption, why is "ctrl"+s mean save? why don't we change it to "shift"+d for "don't want to lose my work"? I mean it is more logical and obvious for newbies...
However "ctrl"+s has been the standard for most programs for a very long time.
When I was using Gimp at the exclusion of Photoshop (Yes I tried using it for a few years to learn it) one of the first things I did was change the curves shortcut to "ctrl"+m, because that is what I was used to in Photoshop and, while I use curves on almost every photograph, I rarely use layer merge.
Having a preset to Photoshop shortcuts as an OPTION would have made things a little easier.

---

### Post by prokoudine on 2011-10-22
> **graphius said:**
> @prokoudine
My rant was about taking away choice.

There wasn't much choice. To the best of my knowledge very few people knew that this file existed anyway.

> **graphius said:**
> Way more serious graphic artists use Photoshop than Gimp. Making it easier for these same artists to switch between Gimp and Photoshop could only be good for Gimp.

Oh, I can argue about that till I'm blue in the face :) Shortcuts are just a tip of the iceberg. There's a **LOT** more to interaction than them. And how about all docs and tuts online that refer to GIMP's shortcuts? You might as well use icons from Photoshop. :)

See, few years ago I made shortcut schemes for Inkscape that mimic AI, Corel DRAW and some other apps. And you know what? It was plain terrible. Every app had a mind of its own, a good chunk of functionaility couldn't be mapped at all, and a lot of what was possible felt just unnatural. It was (and still is) a cripple all around.

My experience with updating PS scheme for GIMP is more or less the same. So no, I seriously refuse to understand how tricking yourself into using shortcuts from another application makes life easier. It simply doesn't make any sense to me. Sorry :) Of course, YMMV.

> **graphius said:**
> The problem I see is devs who say it has to be their way. I am more than willing to admit that devs, especially Gimp developers, have some great ideas, but to throw away an OPTIONAL setting, because it is not "The Gimp Way" seems silly.

Everyone is encouraged to support that outside of GIMP.

> **graphius said:**
> Having a preset to Photoshop shortcuts as an OPTION would have made things a little easier.

As stated before, it wasn't any popular anyway.

---

### Post by jampe on 2011-10-27
prokoudine, I truly do understand and respect that GIMP is an entirely different interface all together. And I recognise that trying to mimic Photoshop could be a bad choice if you want to get to know the program intimately. But if you're just getting used to a lot of new software because you come from a Mac/Windows environment, it's a bit of a mouthful.

Learning to use any interface is a matter of developing habits, meaning there is not one "perfect" way of doing it, and if a shortcut layout reminiscent of earlier experiences facilitates that, it's a totally reasonable thing to do.

Nevertheless, at least we have the choice, and that's the important thing. I was just hoping for some constructive replies, allowing us to further develop the shortcut layout to bridge Photoshop and GIMP nicely. I was never trying to turn one into the other, I meant it as a public experiment.

---

### Post by prokoudine on 2011-10-28
> **jampe said:**
> prokoudine, I truly do understand and respect that GIMP is an entirely different interface all together. And I recognise that trying to mimic Photoshop could be a bad choice if you want to get to know the program intimately. But if you're just getting used to a lot of new software because you come from a Mac/Windows environment, it's a bit of a mouthful.

Which is why I'd rather see more good introductional video tutorials :) And I will probably end up doing some.

> **jampe said:**
> Learning to use any interface is a matter of developing habits, meaning there is not one "perfect" way of doing it,

Quite possibly :)

> **jampe said:**
> Nevertheless, at least we have the choice, and that's the important thing.

Personally I'm grateful to whomever maintains that shortcut scheme :)

---

