---
title: "submitting form in evolution"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by zora123 on 2007-07-12
Hi all,

would someone please help me, i have a question regarding evolution in ubuntu 7.04.

i received an email that actually is a form (html form).
upon completing the form, i clicked the 'submit' button at the bottom of the form.
examining the form properties (viewing the html code), the submit button should send an email to certain account.
but when i clicked this submit button in evolution, nothing happened.

what's the problem?

---

### Post by kyphi on 2007-07-13
When you want to send mail in Evolution it sends it as a text file.  If you want to send it as an HTML file you need to change it to HTML.

In Evolution, go to New, then Format, then HTML.

---

### Post by zora123 on 2007-07-14
the mail i received is an HTML mail indeed.
it is an HTML form
the source looks something like this:

```

<html>
<body>
<form name="form1" method="post" action="server@domain.com">
  Name: <input name="name" type="text" id="name">
  <br />
  <input type="submit" name="Submit" value="Submit">
</form>
</body>
</html>

```

i opened the mail, type my name on the field provided there, and then click the submit button.
but nothing happened.

---

### Post by kyphi on 2007-07-14
You need to insert the HTML form into an email in Evolution (don't forget to change to HTML transmission as outlined earlier) and send it back to where it came from.

The submit button on the form only works if you access this form on line.

---

### Post by zora123 on 2007-07-16
thank you, kyphi, but i dont think you get me right.
it seems that you misunderstood my problem.

the mail i received is a form itself... it's NOT an email with a form file attached to it.

using outlook express (is it allowed to mention non open-source program here? i'm new here, i dont know the rule yet), if i receive that kind of email, whenever i click the submit button after completing the form, outlook express will send a new mail for me with the form data attached to it.

am i confusing?
:cry:

---

### Post by kyphi on 2007-07-17
No, zora123, you are not confusing .... well, a little perhaps.

And, yes, you can mention Microsoft products without causing offence.

If Outlook Express will send your form attached to a new letter, it must do so as an HTML email.

You can do the same thing in Evolution.  If you send from Evolution in text mode, anything you want to send is as an attachment.  If you send via HTML mode then you can embed your form in the body of the email.  So, you have two ways of sending things: Text or HTML.

I will try some experiments and get back to you.

---

### Post by kyphi on 2007-07-17
I accessed Outlook Express and it is as I thought ... you need to make a choice between sending email as either text or HTML - the same as in Evolution.

So, why don't you try it:  Open Evolution, click on New, then Format then HTML, then Insert -> HTML file.

The only difference with Outlook is that you can have HTML activated all the time and send all your emails in that format wheras in Evolution you have to select it as you need it (text files are more secure).

---

### Post by kyphi on 2007-07-17
1.  Place the HTML form that you want to send into your Home folder or on the Desktop.
2.  Open Evolution.
3.  Scroll to the message you received with the HTML form.
4.  Click on the Reply button.
5.  Click on Format and select HTML.
6.  Click on Insert and select HTML File.
7.  Select your HTML form from the dropdown menu.
8.  Click on Open.
9. Click on Send.

Done

If this still does not answer your question you may be better served by accessing Help -> Online Help where you will find the people who specialise in Evolution.

---

### Post by zora123 on 2007-07-18
thanks kyphi.

btw, do you happen to know if there's another email application that can handle this kind of problem?
i'd like to switch to it if there's any.

---

### Post by Rui Pais on 2007-07-18
> **zora123 said:**
> btw, do you happen to know if there's another email application that can handle this kind of problem?
i'd like to switch to it if there's any.

Have you tried thunderbird? or maybe some browser that have an inside mail manager like Opera...

---

### Post by kyphi on 2007-07-18
> btw, do you happen to know if there's another email application that can handle this kind of problem?
i'd like to switch to it if there's any.

Any email programme can send messages in HTML format.  Text format is activated by default because it is more secure.

If you are not happy with Evolution, do try another email programme such as Thunderbird.  You can install it via  Add/Remove from the Applications menu.

I am not familiar with Opera as suggested by Rui Pais.

Have you tried the Help -> Get Help Online in Evolution?

---

### Post by zora123 on 2007-07-19
i had just submitted the question in Help -> Get Help Online in Evolution (launchpad.net)

thanks for your suggestion.
:)

---

