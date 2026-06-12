---
title: "Glassfish v2 on PowerBook G4, IBM Java 6"
date: 2008-03-12
forum: Apple PPC Users
---

### Post by Amaridian on 2008-03-12
Today i made a try installing glassfish v2 on my PowerBook G4 Ti, Gutzi Gibbon, IBM Java 6.

To make it short - Huge Problem :)

when executing the glassfish setup.xml (sudo lib/ant/bin/ant -f setup.xml) i get the following error-message:

> create.domain:
     [exec] Using port 4848 for Admin.
     [exec] Using port 8080 for HTTP Instance.
     [exec] Using port 7676 for JMS.
     [exec] Using port 3700 for IIOP.
     [exec] Using port 8181 for HTTP_SSL.
     [exec] Using default port 3820 for IIOP_SSL.
     [exec] Using default port 3920 for IIOP_MUTUALAUTH.
     [exec] Using default port 8686 for JMX_ADMIN.
     [exec] Domain being created with profile:developer, as specified by variable AS_ADMIN_PROFILE in configuration file.
     [exec] ------ Using Profile [developer] to create the domain ------
     [exec] XML processing for profile: Base document [/opt/glassfish/lib/install/templates/default-domain.xml.template]. Profile name [developer]. Processing property [domain.xml.style-sheets].

     [exec] The file in given locale [de_DE] at: [/opt/glassfish/lib/install/templates/locales/de_DE/index.html] could not be found. Using default (en_US) index.html instead.
     [exec] Security Store uses: JKS
     [exec] File {0} not found.
     [exec] CLI130 Could not create domain, domain1

BUILD FAILED
/opt/glassfish/setup.xml:174: The following error occurred while executing this line:
/opt/glassfish/setup.xml:604: exec returned: 1


Hopefully somebody is a litte bit experienced with glassfish - thank you a lot for any help!

Christian

---

