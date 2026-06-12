---
title: "System fonts all boxes squares rectangles invalid"
date: 2008-09-16
forum: Apple Hardware Users
---

### Post by dwreck86 on 2008-09-16
hi, i installed xubuntu on an imac g3, 6.04, and it was running good. then i let it upgrade to 8.04 and now i have no system fonts. its all boxes/squares/rectangles ive been thru hell and high water tryin to get this mess up :) ive tried surfin the web for help. tried editing the xorg.conf and that doesnt work... any suggestions?


saw this posted somewhere online thought id post it here, im not sure how to do this lol 

I had the same problem, while upgrading from edgy to feisty.
Then I upgraded xfonts-utils first (it contains update-fonts-dir).
This new update-fonts-dir accepts the -x11layout option.

that helped that person out... but im not sure how to do it...

---

