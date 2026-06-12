---
title: "Thunderbird Help"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by namrocks on 2007-05-09
In Windows I could change the fonts in the Thunderbird Folder and Message panes by going to my TB profile, creating a Chrome directory and a userchrome.css file and then typing:

/* Folderpane(color/text) & Messagepane(color) */
treechildren {
background-color: ##D50000 !important;
font-family: Arial !important;
font-size: 17px !important; }

/* Messagepane text */
treechildren:-moz-tree-cell-text(unread) {
font-size: 10pt !important;
font-family : Arial bold !important;
color: #483D8B !important } 

I tried the same thing in Ubuntu - home/my name/thunderbird. I went my profile, created a Chrome directory, a userchrome.css file, etc. Nothing happened. Help. Thanks.

---

### Post by ubnewbie2 on 2007-05-09
have you installed an arial font? I don't think ubuntu comes with one by default.

---

### Post by teddybairs1 on 2007-05-09
Well, Ubuntu isn't Windows and it's not going to respond to the same kinds of command line input.

Where Thunderbird is concerned if you want to change the fonts you can go to Edit-->Preferences-->Display and down at the bottom of the pane is a thing for configuring fonts.

Don't know if this is exactly what you're looking for, but it might at least be a start.

How long have you been using Linux in general, or Ubuntu specifically?

---

### Post by candtalan on 2007-05-09
I do some similar editing in tb in various kubuntu versions and itworks ok.

In kubuntu 7.04 the structure would be I think, for example
/home/username/.mozilla-thunderbird/lxn1ndha.default/chrome/userChrome.css

I note the hidden files and the upper case.

obviously TB must be restarted after such editing.

atypical edit I use is

======================================

/* Folderpane(color/text) & Messagepane(color) */
treechildren {
background-color: #FCE7F2 !important;
font-family: FreeSans !important;
font-size: 10pt !important;
color: #002600 }


/* also try */

treechildren:-moz-tree-cell-text(specialFolder-Drafts),
treechildren:-moz-tree-cell-text(specialFolder-Unsent) {
     font-weight: normal !important;
     color: #FF4B2B !important;
}

======================================

hth

---

### Post by namrocks on 2007-05-09
candtalan, I followed your instructions and they worked perfectly. I never would have figured that out on my own. Thank you. 

ubnewbie2, I did not have a clue until I read your post that Ubuntu fonts and Windows fonts are different. 

teddybairs1, I've been lurking in the shadows on these and other Linux forums for a year or so, wanting to make the move but feeling too ignorant and afraid. I played a little with the Ubunu and Mepis live disks but did not install Ubuntu (or any other Linux distro) until 4/21/07 just after the Feisty final release. It's been a roller coaster of highs and lows, but never boring. I basically had one foot in and one foot out of Ubuntu until a couple of days ago. I can't explain it but something snapped and I fell in love. Windows is no longer an option. I'm not yet ready to use Ubuntu as my main OS as I need a certain level of fucntionality for my office, but I am making progress toward that goal and can see light at the end of the tunnel. These forums have been my primary method of learning and getting my Ubuntu installation ready for prime time.

Thanks to all for your support and suggestions.

---

