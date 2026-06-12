---
title: "firefox / extensions trouble"
date: 2005-12-17
forum: Absolute Beginner Talk
---

### Post by o_owd on 2005-12-17
hi,
i am new to ubuntu and linux.
i downloaded firefox 1.5, folowed the howto guide and managed to install it.
so far so good.
now i am trying to install some extensions and i am getting this message:

"Firefox cound not install the file at [http://[.....]](http://[.....])
because: unexpected installation error
Review the javascript console log for more details."

and in javaconsole:
"Error: installLocation has no properties
Source File: file:///opt/firefox/components/nsExtensionManager.js
Line: 3233"

i have no ideea what the problem is.

sorry for my poor english and thanks in advance !

OJi.

---

### Post by bscbrit on 2005-12-17
Are you sure that the extensions that you are trying to install are designed to work with Firefox 1.5?

---

### Post by o_owd on 2005-12-17
i tried with several extensions.
i uninstalled 1.5 and reinstalled again but without "sudo chown -R username:username /opt/firefox" from the guide and it works.

---

