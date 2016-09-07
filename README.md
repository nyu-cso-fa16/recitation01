# Computer Systems Organization : Recitation 01
-----------------------------------------------

The purpose of these exercises is to get you up and running with the tools and environment you will be using over the course of the semester. 

You will do the following...

* Install the Virtual Machine (VM) 
* Confirm that Git is installed on your VM
* Create a Github repository that is a 'fork' of this 'repository'.
* 'Push' some commits to your new Github repository.   
* Install an editor you will use for C programs.
* Format some C programs for good style.
* Compile and execute two programs in C. 

Detailed instructions on how to do these things are below. 

** For all things that require your email, please use your NYU email only.

Step 1: Virtual Machine
-----------------------

A virtual machine (VM) is an operating system OS or application environment that is installed on a 'host' computer which imitates dedicated hardware. The end user has the (roughtly) same experience on a virtual machine as they would have on dedicated hardware.

You are required to do all labs on the class virtual machine (VM) based on Ubuntu Linux. To get the virtual machine running on your personal desktop or laptop, take the following steps. 

* Download the VirtualBox virtual machine monitor <a href="https://www.virtualbox.org/wiki/Download_Old_Builds_4_3">Version 4.3.30</a> (Please just use version 4.3.30 and not any other version.) Choose the right binary to download according to the type of operating system running on your laptop.  
*  Download the class virtual machine image <a href="http://tintin.news.cs.nyu.edu/lubuntu14.04.ova">here</a>. This file is fairly large (1.1GB), so you need to be patient.  
* Install and launch Virtualbox. On the Virtualbox application toolbar, under the Menu item "File", click on "Import appliance...", and choose the previously downloaded lubuntu14.04.ova file when prompted.  
* Turn off the option "Enable Nested Paging" in the VirtualBox configuration under Settings->System->Acceleration. If this option does not appear or if the checkbox is greyed out then skip it.
* For convenience you can allow yourself to copy text from the host OS (your windows or mac) to the guest OS (the OS in the VM). To do this go to Settings->General and in the "Advanced" tab, set "Shared Clipboard" and "Drag'n'Drop" to "Bidirectional".
* After importing, start the virtual machine named "lubuntu" and log in using the username and password given in Piazza).
* Open the Devices menu option and click 'Insert guest additions CD image.' A disk will be mounted that you can find by click the little file icon in the bottom left portion of the screen. Click autorun.sh and execute this script. This will give you better screen resolution.    

If you wish to use your own existing Linux-based desktop or laptop instead of the class virtual machine, that is fine. But note that we will not be debugging any problems you might have. There simply isn't time or expertise.

If you run into problems (particularly likely with Windows users) see this [troubleshooting guide](http://cs.nyu.edu/courses/spring16/CSCI-UA.0201-001/resources/vm-troubleshoot.html)

Step 2: Git & Github 
--------------------

Git is a “version control system”. It provides, among other things, change tracking for source files. It comes preinstalled on your VM. 

* You can test the install of git on your system by running the command `git` from terminal (Start Menu > Accessories > LXTerminal). You should see usage information.
* Run the following commands from terminal:<br>
   ```git config --global user.email "you@nyu.edu"```<br>
   ```git config --global user.name "Your Name"```<br>
   (The email should be the same email you used to register your github account)

Github is Git hosting service. This means they run the servers that host our remote Git repositories. A repository is just  some some source code organized into a collection. 

Github has donated an 'organization' for our class. An organization is just a private site for us to share repositories as a group. Our organization is called 'nyu-cso-fa16'.

Github will contain repositories for each of homeworks, in-class code, etc. We will effectively download the code from Git to work on it, then we will upload the code back to Github so it can be graded. We will be dooing this all with git commands on the command line.

* If you are unfamiliar with Git, watch the [first two git basics video](http://git-scm.com/videos).
* If you are unfamiliar with Github, watch [this YouTube video](https://www.youtube.com/watch?v=0fKg7e37bQE).
* A [simple git cheatsheet](http://rogerdudler.github.io/git-guide/). 
* A [complete reference](http://www.git-scm.com/book/en/v2).

More on Git & Github will be covered in recitation.

Step 3: Fork the recitation01 repository and push a commit
--------------------------------------------------

You should have received an email from Github notifying you that you have been added to the 'nyu-cso-fa16' organization. This means you have access to class repositories. This is where you will get your lab assignments as well as code used in class.

* In your VM, open a browser to this respository.
* Click the 'Fork' button on the top right corner. Select your username as the fork destination.
* Once the repo is created, Look at the lower right-hand corner of your screen, you should see a "clone url" section. Click HTTPS and then copy to your clipboard the 'HTTPS clone URL' from the lower right text box on the screen.
* Choose a place on your VM for your homeworks to reside and open a terminal to that location.
* Execute the following series of commands: <br/>
  ```git clone https://github.com/<YOUR-GITHUB-USERNAME>/recitation01.git```<br/>
  ```cd recitation01   ```<br/>
  ```>cso-rocks.txt   ```<br/>
  ```git add cso-rocks.txt    ```<br/>
  ```git commit -m "First commit" cso-rocks.txt   ```<br/>
  ```git push origin master   ```<br/>  

You should now see a file 'cso-rocks.txt' on the Github page for your fork of the recitation01 repository. 

Step 4: Install Sublime (Optional)
----------------------------------

We will need some editor into which we will write code. You can choose whatever editor you want, however we are going to stay away from full fledged IDE's for the most part during this course, we want to become command-line masters!

The obvious choices, VIM and Emacs are somewhat challenging to learn (though very powerful when you do!). So if you are not familiar with them, I suggest you use [Sublime 2](https://www.sublimetext.com/). Its easy to use and provides a number of nice features for developers. 

* In your VM, open a terminal and run the following series of commands<br/>
  ```sudo add-apt-repository -y ppa:webupd8team/sublime-text-2  ```<br/>
  ```sudo apt-get update  ```<br/>
  ```sudo apt-get install sublime-text  ```<br/>


Step 5: Install Astyle
----------------------

AStyle is a code formatter that works for many languages including C. Since the style of your code will be a factor in your grade, you should get in the habit of using this tool regularly.

* In your VM, open a terminal and run the following series of commands<br/>
  ```sudo apt-get install astyle  ```
* Confirm success by running the command from a terminal ```astyle``` (You should see the message 'Artistic Style has terminated')
* In Sublime open both the .c files in the root of the directory repository.
* In the root of the directory where you cloned the repository run the command<br/>
  ```astyle --suffix=none --style=allman *  ```
* Have Submlime reload those files. You should see that they are are now formatted nicely.


Step 6: 'Hello World'   
---------------------

You use the C compiler command `gcc`, to compile C programs. gcc comes preinstalled on your VM. 

gcc, as well as many key pieces of development software (e.g. the C library, make), have been developed by [GNU](http://www.gnu.org/). That's why you hear people sometimes refer to GNU/Linux since strictly speaking, Linux is just the kernel of the OS and not the complete system.

* Open and read the comments in `basic.c`
* Compile the `basic.c` C file, type `gcc basic.c` in the terminal. This generates an executable `a.out`. 
* Execute it by typing `./a.out`
* Repeat the above three steps for `standard.c`
* Execute the following series of commands: <br/>
  ```git add .    ```<br/>
  ```git commit -am "C programs formatted executed!"   ```<br/>
  ```git push origin master   ```<br/>  
