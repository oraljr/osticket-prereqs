<p align="center">
<img src="https://i.imgur.com/Clzj7Xs.png" alt="osTicket logo"/>
</p>

<h1>osTicket - Prerequisites and Installation</h1>
This tutorial outlines the prerequisites and installation of the open-source help desk ticketing system; osTicket.<br />



<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Internet Information Services (IIS)

<h2>Operating Systems Used </h2>

- Windows 10</b> (22H2)

<h2>List of Prerequisites</h2>

- Azure Virtual Machine
- Internet Information Services (IIS)
- PHP Manager
- Rewrite Module
- VC Redist
- MySQL
- Heidi SQL
- osTicket v1.15.8
- Link to downloads: https://drive.google.com/drive/u/0/folders/1APMfNyfNzcxZC6EzdaNfdZsUwxWYChf6


<h2>Installation Steps</h2>


The first thing you'll do is create a virtual machine (VM) by going to https://portal.azure.com/. Setup your virtual machine with Windows 10 Pro, version 22H2. You'll want to choose a virtual machine with atleast 2 vcpus and 16 gbs of memory.

Once your VM is fully deployed you'll want to conncet to it with the public ip address the VM is setup with. You'll connect through the remote desktop connection app. (For Mac users you can install Microsoft remote desktop from the app store)

![image](https://github.com/oraljr/osticket-prereqs/assets/152557529/ce86b57f-3ea1-4c07-9bcb-9c5e019663be)

</p>
<br />

<p>
<img src="https://imgur.com/MAhXK2e.png" height="80%" width="80%" alt="Disk Sanitization Steps"/>
</p>
<p>
<p>
<img src="https://imgur.com/Zf2jw07.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Once you've logged in with the username and password you created for your VM in Azure and connected to your VM, you'll go to: control panel -> programs -> Turn Windows features on and off.

<p>
<img src="https://imgur.com/fGXMpx4.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/LBGkAw6.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
You'll want to install / enable IIS in Windows with CGI and Common HTTP Features.
   World Wide Web Services -> Application Development Features -> 
[X] CGI
[X] Common HTTP Features
  
<p>
<img src="https://imgur.com/LQjw9le.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/pbPeHb1.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
***NOTE*** Make sure all Common HTTP Features are checked.
 
 To test if IIS is installed properly, open browser of your choice and search 127.0.0.1 in your address bar. 
  It should look something like this. 
  
<p>
<img src="https://imgur.com/eICujoq.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
  
  
Now that IIS is enabled, download and install PHP Manager for IIS (PHPManagerForIIS_V1.5.0.msi) from the Installation Files.
  Go through the install wizard and complete the install.
  
Next from the Installation Files, download and install the Rewrite Module (rewrite_amd64_en-US.msi)
  
Create a folder in the C drive named PHP.
  
From the Installation Files, download PHP 7.3.8 (php-7.3.88-nts-Win32-VC15-x866.zip) and unzip the contents into C:\PHP
  
(_**NOTE**_ If this appears, choose to “Keep” the file:)
  
<p>
<img src="https://imgur.com/xZv1Yhw.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/YwBhqo0.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

Next you'll download and install VC_redist.x86.exe from the installation files. Go through the setup wizard to complete install.
Download and install MySQL 5.5.62 (mysql-5.5.62-win32.msi)
  Run the setup wizard:
Typical Setup ->
Launch Configuration Wizard (after install) ->
Standard Configuration ->

  Choose a new root password
  
<p>
<img src="https://imgur.com/KxcUy7C.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Execute the process on the next page.
  
<p>
<img src="https://imgur.com/i7sn6hT.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Next you'll search for IIS in the windows search bar. Right click and Open IIS as an administrator.
  The program should look like this.
  
<p>
<img src="https://imgur.com/rgdZwmM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Now we'll register PHP from within IIS.
  Click on PHP Manager ->
  
<p>
<img src="https://imgur.com/vvTLNBH.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Register new PHP version. ->
  
<p>
<img src="https://imgur.com/qdbn5zQ.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Then you'll provide a pathway to the php executable file (php-cgi.exe). 
  Go to C Drive -> PHP -> click on php-cgi file.
  
<p>
<img src="https://imgur.com/oJZ0gp9.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Restart the IIS server.
  
<p>
<img src="https://imgur.com/CJ3RUbG.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Next you'll install osTicket v1.15.8. First download osTicket from the Installation Files Folder. Once thats complete, open the folder to find a folder labeled "upload". Copy 'upload' to c:\inetpub\wwwroot. Within wwwroot folder, rename "upload" to "osTicket"
  
  Restart IIS again.
  
On IIS go to sites -> Default -> osTicket and on the right, select “Browse *:80”
  
<p>
<img src="https://imgur.com/Yw55d5b.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

  
<p>
<img src="https://imgur.com/eJIsGTn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

If you see this screen, that mean osTiscket is working! Great job, you've eraned a deep breath! Now, lets continue.
  
  Some extensions wil not be enabled on the osTicket browser. Next you'll manually enable a few extensions in IIS for them to work. 
  To enable the extensions:
  Go back to IIS, sites -> Default -> osTicket
  -Double click PHP manager
  -Select "Enable or disable an extension"
  
<p>
<img src="https://imgur.com/vvTLNBH.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/uigyKjb.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  You'll want to right click to enable the three following extensions:
  
  1.) php_imap.dll
 
  2.) php_intl.dll
  
  3.) php_opcache.dll
  
<p>
<img src="https://imgur.com/cOem7Nb.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>

![image](https://github.com/oraljr/osticket-prereqs/assets/152557529/d8003608-9845-4a2e-a243-b3a1d4c68bd8)

Refresh the osTicket site in your browser, observe the changes of the extensions you enabled.
  
Now, you're are going to rename one of the files in your osTicket folder.
  Go into the file explorer and search for C:\inetpub\wwwroot\osTicket\include\ost-sampleconfig.php
  
  You're going to rename ost-sampleconfig.php to ost-config.php

  ![image](https://github.com/oraljr/osticket-prereqs/assets/152557529/ffa05972-aff7-4cd6-a5ab-fe210b1c10fd)
  
  Next you'll right click on the ost-config.php file and go to properties -> security -> advanced, and disable the inheritance. Then select Remove all inherited permissions from this object.
  
  Next you'll add new permissions.
  
  Select Add
  
<p>
<img src="https://imgur.com/VPZvOdo.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
Select a principal
  
<p>
<img src="https://imgur.com/PoGk34d.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  
 Type "everyone" in the box.
  
<p>
<img src="https://imgur.com/F4H3ppM.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Make sure all accessible boxes are checked.
  
<p>
<img src="https://imgur.com/rbbGqwB.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Select apply and Ok.
  
<p>
<img src="https://imgur.com/saRO3y5.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  Next you'll continue to setup osTicket within the browser. Click Continue on the osTicket browser page. Name your Help Desk, add an emial to recieve eamil from customers and fill in the remaining as required (you'll save the Database Settings for later). 
  
  Next you'll download and install HeidiSQL from the Installation Files. 
  
<p>
<img src="https://imgur.com/i7a4gWC.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  When the program is launched you'll create a new session.
  
<p>
<img src="https://imgur.com/g5M1i61.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Make sure the username is root and enter the password you chose when you set up the server.
  
<p>
<img src="https://imgur.com/LEAZNOc.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  Once you're connected to the session you will finish setting up back on the browser. Under Database Settings, the browser the username will be 'root' and the password will be Password1.
  
  Next you'll create a new database for osTicket in HeidiSQL. Right click on the left side where is says "Unnamed", select "create new", then select "database". Name the new database 'osTicket'. Once you have the new database setup go back to the osTicket browser and under MySQL Database fill in 'osTicket'.

![image](https://github.com/oraljr/osticket-prereqs/assets/152557529/9afcd4bb-99bd-492b-9372-4d3a54740a58)
  
<p>
<img src="https://imgur.com/0rG1AJm.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  The penultimate step is some cleaning up. You be deleting the '**setup**' folder from your system. Got to the C drive -> inetpub -> wwwroot -> osTicket -> select setup and delete setup folder _**only**_.
  
  Next you'll set the permissions back to "Read" only for the ost-config.php file. C drive -> C drive -> inetpub -> wwwroot -> osTicket -> include -> right click ost-config.php and rest permissions to Read & execute and Read.
  
<p>
<img src="https://imgur.com/wFr0pkK.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
<p>
<img src="https://imgur.com/jsJOPyn.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  The final step is to login to osTicket on the browser.
  
<p>
<img src="https://imgur.com/uHVdDsx.png" height="40%" width="40%" alt="Disk Sanitization Steps"/>
</p>
<p>
  
  You did it! You have now successfully installed and setup osTicket!
