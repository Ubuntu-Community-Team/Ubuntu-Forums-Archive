---
title: "Exporting photos in digiKam"
date: 2009-11-23
forum: Art &amp; Design
---

### Post by humphreybc on 2009-11-23
So I want to upload some photos to Facebook out of my digiKam library. They need to be resized. I use the Facebook upload plugin in digiKam, which works fine - but for some reason the photos are not in the correct orientation, even though they are under the digiKam gallery. I presume it's something to do with digiKam picking up and acting on the camera orientation EXIF data and Facebook not.

So, I decided I would just export my selected photos to a folder, resized, and then manually upload them.

BUT what the hell? There is no "export to folder" option under digiKams' "export" menu!

Then I found an option to resize them (Tools > Resize Images), so I selected this and then set my output folder as my desktop. It worked, but I got an error message after each photo saying that "Desktop" was not in the list of folders so could not be imported into digiKam Album... so does this mean that I cannot export photos outside of my selected "watched" folders?

Aside from the error messages, where I just clicked "continue" on each message - I got my 9 photos exported and resized to the desktop. I then uploaded them manually to find that they were rotated wrongly on Facebook - even though they appeared fine on my desktop, and in gThumb!

Is this a problem with digiKam, or Facebook? How can I set the orientation manually in digiKam (instead of relying on EXIF data) so that Facebook will orientate them properly when I upload them?

Thanks for reading all that!

Cheers,
Benjamin

---

### Post by kayosiii on 2009-11-25
> **humphreybc said:**
> So I want to upload some photos to Facebook out of my digiKam library. They need to be resized. I use the Facebook upload plugin in digiKam, which works fine - but for some reason the photos are not in the correct orientation, even though they are under the digiKam gallery. I presume it's something to do with digiKam picking up and acting on the camera orientation EXIF data and Facebook not.

So, I decided I would just export my selected photos to a folder, resized, and then manually upload them.

BUT what the hell? There is no "export to folder" option under digiKams' "export" menu!

Then I found an option to resize them (Tools > Resize Images), so I selected this and then set my output folder as my desktop. It worked, but I got an error message after each photo saying that "Desktop" was not in the list of folders so could not be imported into digiKam Album... so does this mean that I cannot export photos outside of my selected "watched" folders?

Aside from the error messages, where I just clicked "continue" on each message - I got my 9 photos exported and resized to the desktop. I then uploaded them manually to find that they were rotated wrongly on Facebook - even though they appeared fine on my desktop, and in gThumb!

Is this a problem with digiKam, or Facebook? How can I set the orientation manually in digiKam (instead of relying on EXIF data) so that Facebook will orientate them properly when I upload them?

Thanks for reading all that!

Cheers,
Benjamin

This one is quite easy to work around. Digikam doesn't see files outside of a few specially blessed folders. This will usually be your Pictures folder if you create a link to your desktop folder inside the Pictures folder. Digikam will now be able to see that folder.

As for the exif being wrong for the facebook plugin... the facebook plugin is a kipi plugin... [http://www.kipi-plugins.org/drupal/](http://www.kipi-plugins.org/drupal/) you should probably enquire there about the bug.

---

