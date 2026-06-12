---
title: "JSP Error"
date: 2007-03-12
forum: Absolute Beginner Talk
---

### Post by jjoberg on 2007-03-12
I am not sure what I am doing wrong, but when I try to log into my T. Rowe. Price account using Firefox i get redirected to an error page.

> JSP Processing Error
HTTP Error Code:   500

Error Message:

JSPG0049E: /pages/accountAccess/desktop/browserWarn.jsp failed to compile : 
JSPG0091E: An error occurred at line: 38 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:104: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("brsNm")) );
               ^
JSPG0091E: An error occurred at line: 39 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:106: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("pltNm")) );
               ^
JSPG0091E: An error occurred at line: 193 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:150: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("brsNm")) );
               ^
JSPG0091E: An error occurred at line: 193 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:152: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("brsVr")) );
               ^
4 errors

Root Cause:

com.ibm.ws.jsp.JspCoreException: JSPG0049E: /pages/accountAccess/desktop/browserWarn.jsp failed to compile : 
JSPG0091E: An error occurred at line: 38 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:104: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("brsNm")) );
               ^
JSPG0091E: An error occurred at line: 39 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:106: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("pltNm")) );
               ^
JSPG0091E: An error occurred at line: 193 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:150: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("brsNm")) );
               ^
JSPG0091E: An error occurred at line: 193 in the file: /pages/accountAccess/desktop/browserWarn.jsp
JSPG0093E: Generated servlet error from file: /pages/accountAccess/desktop/browserWarn.jsp 
/apps/WebSphere6/profiles/cell102N2/temp/cell102N2/as_cell102z_02/ea_aw1_account_access_web/AAWAccountAccess.war/pages/accountAccess/desktop/_browserWarn.java:152: cannot resolve symbol
symbol  : method validateShortAlphaNum (java.lang.String)
location: class com.ibm._jsp._browserWarn
    out.print( validateShortAlphaNum(request.getParameter("brsVr")) );
               ^
4 errors
	at com.ibm.ws.jsp.webcontainerext.JSPExtensionServletWrapper.translateJsp(JSPExtensionServletWrapper.java(Compiled Code))
	at com.ibm.ws.jsp.webcontainerext.JSPExtensionServletWrapper._checkForTranslation(JSPExtensionServletWrapper.java(Compiled Code))
	at com.ibm.ws.jsp.webcontainerext.JSPExtensionServletWrapper.checkForTranslation(JSPExtensionServletWrapper.java(Compiled Code))
	at com.ibm.ws.jsp.webcontainerext.JSPExtensionServletWrapper.handleRequest(JSPExtensionServletWrapper.java(Compiled Code))
	at com.ibm.ws.webcontainer.webapp.WebAppRequestDispatcher.forward(WebAppRequestDispatcher.java(Compiled Code))
	at org.apache.struts.action.RequestProcessor.doForward(RequestProcessor.java(Compiled Code))
	at org.apache.struts.action.RequestProcessor.processForwardConfig(RequestProcessor.java(Compiled Code))
	at com.trp.jvl.iiwc.translator.struts.TAMStrutsBaseRequestProcessor.processForwardConfig(TAMStrutsBaseRequestProcessor.java(Compiled Code))
	at org.apache.struts.action.RequestProcessor.process(RequestProcessor.java(Compiled Code))
	at org.apache.struts.action.ActionServlet.process(ActionServlet.java(Inlined Compiled Code))
	at org.apache.struts.action.ActionServlet.doGet(ActionServlet.java(Compiled Code))
	at javax.servlet.http.HttpServlet.service(HttpServlet.java(Compiled Code))
	at javax.servlet.http.HttpServlet.service(HttpServlet.java(Compiled Code))
	at com.ibm.ws.webcontainer.servlet.ServletWrapper.service(ServletWrapper.java(Compiled Code))
	at com.ibm.ws.webcontainer.servlet.ServletWrapper.handleRequest(ServletWrapper.java(Compiled Code))
	at com.ibm.ws.webcontainer.webapp.WebApp.handleRequest(WebApp.java:3071)
	at com.ibm.ws.webcontainer.webapp.WebGroup.handleRequest(WebGroup.java:236)
	at com.ibm.ws.webcontainer.VirtualHost.handleRequest(VirtualHost.java:210)
	at com.ibm.ws.webcontainer.WebContainer.handleRequest(WebContainer.java(Compiled Code))
	at com.ibm.ws.webcontainer.channel.WCChannelLink.ready(WCChannelLink.java(Compiled Code))
	at com.ibm.ws.http.channel.inbound.impl.HttpInboundLink.handleDiscrimination(HttpInboundLink.java(Compiled Code))
	at com.ibm.ws.http.channel.inbound.impl.HttpInboundLink.handleNewInformation(HttpInboundLink.java(Compiled Code))
	at com.ibm.ws.http.channel.inbound.impl.HttpICLReadCallback.complete(HttpICLReadCallback.java(Compiled Code))
	at com.ibm.ws.tcp.channel.impl.WorkQueueManager.requestComplete(WorkQueueManager.java(Compiled Code))
	at com.ibm.ws.tcp.channel.impl.WorkQueueManager.attemptIO(WorkQueueManager.java(Compiled Code))
	at com.ibm.ws.tcp.channel.impl.WorkQueueManager.workerRun(WorkQueueManager.java(Compiled Code))
	at com.ibm.ws.tcp.channel.impl.WorkQueueManager$Worker.run(WorkQueueManager.java(Compiled Code))
	at com.ibm.ws.util.ThreadPool$Worker.run(ThreadPool.java(Compiled Code))



If any one has any suggestions, I would really appreciate it.  Is this a problem on my end or on the server end?

---

### Post by Paul41 on 2007-03-13
It looks like a problem on their end. HTTP Error Code: 500 is a server error. The error message also points to it being their problem. I would send them this error message in a email and see if they can fix it.

---

### Post by jjoberg on 2007-03-13
Thanks Paul.  I shot them an email over the weekend and I am awaiting a response from them.  The weird thing is that it works in Firefox  on my Windows machine with no problem which was making me think there could be something I was overlooking when I installed Ubuntu.  I used RedHat a long time ago maybe around 2000, or 2001, and now I have become very jaded with all the technology.

---

### Post by Paul41 on 2007-03-13
That is strange. Since it is a server error it shouldn't have anything to do with your browser. I guess it could be an error in there error page telling you that you can't use Firefox or Linux or something like that. I guess only they can say for sure :) .

---

