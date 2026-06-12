---
title: "Why can I not input numbers at this site"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2008-02-24
Why is it that I can not input telephone numbers to search to see if Verizon DSL service is available at the entered phone number at this Verizon site ?

[http://www22.verizon.com/content/consumerdsl/BridgeStandard/BridgeStandard.htm?promotion_code=VZBNR/W28xp1_id=768kp](http://www22.verizon.com/content/consumerdsl/BridgeStandard/BridgeStandard.htm?promotion_code=VZBNR/W28xp1_id=768kp)

I am using Gutsy with Firefox.

Thanks.

---

### Post by rapiscan on 2008-02-24
Those input fields have a bit of javascript code tied with them:
```
onkeypress="javascript:CaptureEnterKey1(event);"
```

Presumably the javascript is failing in firefox or preventing the numbers from being entered into the field.  I didn't see anything output in the error console in firefox though.

---

### Post by billgoldberg on 2008-02-24
Doesn't work on firefox 3 beta 3 neither.

I guess it's one of those IE optimized sites.

---

### Post by rapiscan on 2008-02-24
I was able to get it to work by disabling javascript

Edit->Preferences->Content Tab->Enable Javascript

Then fill in the number.  Then re-enable javascript and hit the submit button.

---

### Post by r4ik on 2008-02-24
Might be i don't understand the question if so please ignore but here,

[http://www22.verizon.com/content/ConsumerDSL/](http://www22.verizon.com/content/ConsumerDSL/)

you can.

---

### Post by kooolrock on 2008-02-24
> **wpshooter said:**
> Why is it that I can not input telephone numbers to search to see if Verizon DSL service is available at the entered phone number at this Verizon site ?

[http://www22.verizon.com/content/consumerdsl/BridgeStandard/BridgeStandard.htm?promotion_code=VZBNR/W28xp1_id=768kp](http://www22.verizon.com/content/consumerdsl/BridgeStandard/BridgeStandard.htm?promotion_code=VZBNR/W28xp1_id=768kp)

I am using Gutsy with Firefox.

Thanks.
do u hv** *No script* for Firefox** installed??

---

### Post by rapiscan on 2008-02-24
No Script would actually allow him to enter the numbers.  The problem is that he does have javascript enabled, and the function call is failing.  As mentioned above, you can temporarily disable javascript to get the form to work.

---

### Post by y-lee on 2008-02-24
> Why is it that I can not input telephone numbers to search to see if Verizon DSL service is available at the entered phone number at this Verizon site ?


Complain about it. I did and sent them a link to this post. Go to [Verizon's site]("http://www22.verizon.com/content/ConsumerDSL/") and click  **Site Feedback** on the bottom of the screen. Web sites that don't work properly in Firefox are unacceptable and unprofessional :(


**Edit**: BTW, site feedback link requires Javascript to be enabled.

---

### Post by wpshooter on 2008-02-24
> **rapiscan said:**
> I was able to get it to work by disabling javascript

Edit->Preferences->Content Tab->Enable Javascript

Then fill in the number.  Then re-enable javascript and hit the submit button.

When I do that then I CAN enter the numbers at the Verizon site but then the search function of this Ubuntu forum site does not work correctly, i.e. I do not get the drop-down menu.

Thanks.

---

### Post by rapiscan on 2008-02-24
wpshooter,

You definitely want to re-enable javascript for the rest of your browsing experience.  I was just recommending temporarily disabling javascript if you really needed to enter the numbers in the form.  You would have to re-enable javascript to submit the form anyway.

---

### Post by wpshooter on 2008-02-24
> **rapiscan said:**
> wpshooter,

You definitely want to re-enable javascript for the rest of your browsing experience.  I was just recommending temporarily disabling javascript if you really needed to enter the numbers in the form.  You would have to re-enable javascript to submit the form anyway.

Thanks.

I also submitted a request to Verizon that they fix this problem.

---

