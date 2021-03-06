# Getting Started with the Raspberry Pi

<iframe class="getting-started-vid" src="//player.vimeo.com/video/108930903?title=0&amp;byline=0&amp;portrait=0" style="width:100%" height="456px" frameborder="0" webkitallowfullscreen mozallowfullscreen allowfullscreen></iframe>

## What You'll Need

* A [Raspberry Pi][rpi-all-models-link]. Note you can use the Raspberry Pi B, B+ and A+. If you want to use the new Raspberry Pi 2, have a look at [Getting Started with RPI2](/pages/gettingStarted-RPI2.md).

* A 4GB or larger SD card. Check what kind of media your device accepts - e.g. a
  [Raspberry Pi B+][rpi-b-plus] uses Micro SD cards whereas older
  [Raspberry Pi][rpi]'s use standard SD cards. The [speed class][speed_class] of
  the card also matters - this determines its maximum transfer rate. We strongly
  recommend you get hold of a class 10 card or above.

* An ethernet cable or [WiFi adapter][wifi] to connect your device to the
  internet.

* Some awesome ideas to hack on! If you need inspiration, check out our
  [projects][projects] page.

__NOTE:__ If you're not experienced with [git][git], check out the excellent
[Try Git][try-git] course at [Code School][code-school].

## Signing Up

Enter your details on the [sign up page][signup]. There are a couple of
restrictions:-

* The username can only contain letters and numbers.
* The password has to be at least 8 characters long.

## SSH Key

![Add SSH Key](/img/screenshots/add_ssh_key.png)

SSH keys use the power of [public-key cryptography][pub_key_crypto] to secure
your connection when sending your code to us. In order to secure your [git][git]
connection, we need your __public__ [SSH Key][ssh_key] (you must never share
your *private* key with anyone.)

Once generated, SSH keys are easy to use. In fact you generally don't have to
think about it at all, once you're set up just `git push` your code to us and
it's taken care of automatically.

In order to generate a key pair for your platform we recommend you take a look
at [Github][github]'s [excellent documentation][github_ssh] on the subject.

### Import From GitHub

For convenience we provide the ability to import your public SSH key from
[GitHub][github] - just click on the Octocat icon in the bottom right-hand
corner ([we use][github_ssh_blogpost] GitHub's [public APIs][github_apis] to
retrieve this data.)

## Creating Your First Application

<!-- ![Creating an Application](/img/screenshots/applications_empty.png) -->
![Creating an Application](/img/gifs/createapp.gif)


The two key components you will interact with in resin.io are *applications* and
*devices* - applications represent the code you want to run on your devices, and
devices the actual hardware itself.

You can have as many devices connected to an application as you like - when you
push code it deploys to every device that application owns.

To create your first application simply type in a name and tap create which will
take you to its dashboard:-

## Adding Your First Device

<!-- ![Empty Application Page](/img/screenshots/application_empty.png) -->
![Empty Application Page](/img/gifs/download-image.gif)

This is the application dashboard where all of the devices connected to your
application will be shown along with their status and logs.

Click the `Download Zip File` button to get the resin.io image for your
application. A dialog will appear prompting you to specify how your device
connects to the internet - either via an ethernet cable or wifi, in which case
you can specify your Wifi network's SSID and passphrase:-

![Wifi Settings](/img/gifs/download-image-Wifi.gif)


While the zip file downloads ensure your SD card is formatted in [FAT32][fat32]
([WikiHow][wikihow] has [instructions][wikihow_format] on how to do this) and
expand the zip file onto it.

![unzip and expand](/img/gifs/unzip-image.gif)

## Setting Up Your Device

Put the SD card into your device, connect either the ethernet cable or insert the usb wifi dongle. Now power up the device by inserting the usb cable and wait for it to appear on the application
dashboard.

![insert SD](/img/gifs/insert-sd.gif)

While you wait resin.io is partitioning your SD card, installing a custom linux
environment and establishing a secure connection with our servers.

If you have a class 10 SD card and a fast internet connection your device should
appear on the dashboard in around 7 minutes. Note that Class 4 SD cards can
take up to 3 times longer so it's well worth investing in the fastest card you
can find.

If you encounter issues with your Raspberry Pi refusing to boot to the SD card, it may be because the SD card was not formatted properly. For best results, it is recommended that you use the [SD Card Formatter][sdformatter] utility from the SD Association.

## Running Code On Your Device

![git pushing](/img/screenshots/git_pushing.png)

A good first project is our [text to speech app][example_app] written in node.js. To clone it, run
the following in a terminal:-

```
git clone https://github.com/resin-io/text2speech.git
```

Once the repo is cloned, cd into the newly created text2speech directory and add the resin git endpoint by running the `git remote add` command shown in
the top-right corner of the application page, e.g.:-

```
cd text2speech

git remote add resin git@git.resin.io:joebloggs/skynet.git
```

Now you can simply run `git push resin master` and push your code up to our servers, where it will distribute it to your
device(s). If this fails, you may need to force the push by running `git push resin master --force`

__NOTE:__ On your very first push, git may ask you if you would like to add this host to your list of allowed hosts. Don't worry about this, just type 'yes' and carry on your merry way.

You'll know your code has been successfully compiled and built when our
friendly unicorn mascot appears in your terminal:-

![git pushing](/img/screenshots/git_pushed.png)

The terminal will also say:
```
-----> Image created successfully!
-----> Uploading image..
       Image uploaded successfully!
```
This means your code is safely on our servers and will be downloaded and executed by all the devices you have connected to your application. You may have to wait a little while for the code to start running on your devices, you can see the progress of the device code updates on the device dashboard:-

![Code updating](/img/screenshots/rpi-app-updating.png)

You should now have a friendly talking raspberry pi and a good base to start building and deploying awesome connected devices.

If node.js isn't your thing, then don't worry, you can use any language you like. Have a look at how to use [dockerfiles][dockerfile] and play around with our python example over [here][python-example].

## Further Reading

* For more details on deploying to your devices, see the [deployment guide][deploy].

* If you need more details on managing your devices and applications, check out
  our [device and application management guide][managing_devices_apps].

## Feedback

If you find any issues with the application, please click the feedback label on
the bottom right-hand side of the page and let us know! We are always open to
feedback and respond to any issues as soon as we can.

[deploy]:/pages/deployment.md
[projects]:/pages/projects.md
[managing_devices_apps]:/pages/managingDevicesApps.md
[wifi]:/pages/wifi.md
[supported]:/pages/devices.md
[dockerfile]:/pages/dockerfile.md

[alpha]:http://en.wikipedia.org/wiki/Alpha_software#Alpha
[speed_class]:http://en.wikipedia.org/wiki/Sd_card#Speed_class_rating
[signup]:http://alpha.resin.io/signup
[git]:http://git-scm.com/
[ssh_key]:http://en.wikipedia.org/wiki/Secure_Shell
[pub_key_crypto]:http://en.wikipedia.org/wiki/Public-key_cryptography
[github]:http://github.com/
[github_apis]:https://developer.github.com/v3/
[github_ssh]:https://help.github.com/articles/generating-ssh-keys
[github_ssh_blogpost]:http://resin.io/blog/email-github-public-ssh-key/
[login]:http://alpha.resin.io/login
[wikihow_format]:http://www.wikihow.com/Format-an-SD-Card
[wikihow]:http://www.wikihow.com/Main-Page
[fat32]:http://en.wikipedia.org/wiki/Fat32#FAT32
[sdformatter]:https://www.sdcard.org/downloads/formatter_4/
[example_app]:https://github.com/resin-io/text2speech
[try-git]:https://www.codeschool.com/courses/try-git
[code-school]:https://www.codeschool.com/
[rpi]:http://www.raspberrypi.org/
[rpi-b-plus]:http://www.raspberrypi.org/products/model-b-plus/
[python-example]:https://github.com/alexandrosm/hello-python
[rpi-all-models-link]:http://www.raspberrypi.org/products/