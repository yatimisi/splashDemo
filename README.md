# ionic 4 - Splash Screen Demo

## Demo run

```cmd
First clone and cd this repositorie.

$ npm install

$ ionic serve -l
...(Y/n)? [Y]
```


## Generation step

### 1. start demo
```cmd
$ ionic start splashDemo sidemenu
```

### 2. generation resources for ios and android
```cmd
$ ionic cordova prepare ios

$ ionic cordova prepare android
```

### 3. Update the Default Splash Screen Config
/config.xml
```xml
...
<preference name="BackupWebStorage" value="none" />

<preference name="FadeSplashScreenDuration" value="300" />
<preference name="SplashScreenDelay" value="10000" />
<preference name="AutoHideSplashScreen" value="true" />
<preference name="FadeSplashScreen" value="true" />
<preference name="ShowSplashScreen" value="false" />

    <platform name="android">
...
```

### 4. hide and show the animation
src/app/app.component.html
```html
<ion-app>

  <div *ngIf="showSplash" class="splash">
    <div *ngIf="showSplash" class="sk-fading-circle">
      <div class="sk-circle1 sk-circle"></div>
      <div class="sk-circle2 sk-circle"></div>
      <div class="sk-circle3 sk-circle"></div>
      <div class="sk-circle4 sk-circle"></div>
      <div class="sk-circle5 sk-circle"></div>
      <div class="sk-circle6 sk-circle"></div>
      <div class="sk-circle7 sk-circle"></div>
      <div class="sk-circle8 sk-circle"></div>
      <div class="sk-circle9 sk-circle"></div>
      <div class="sk-circle10 sk-circle"></div>
      <div class="sk-circle11 sk-circle"></div>
      <div class="sk-circle12 sk-circle"></div>
    </div>
  </div>

  <ion-split-pane>
...
```
[animation resources](http://tobiasahlin.com/spinkit/)

src/app/app.component.ts
```typescript
import { timer } from 'rxjs';

...

@Component({
  selector: 'app-root',
  templateUrl: 'app.component.html',
  styleUrls: ['app.component.scss']
})
export class AppComponent {
  showSplash = true;

...

  initializeApp() {
    this.platform.ready().then(() => {

      this.statusBar.styleDefault();
      this.splashScreen.hide();

      timer(3000).subscribe(() => this.showSplash = false)
    });
  }
```

### 5. animation Styles
/src/app/app.component.scss
```css
.splash {
    position: absolute;
    width: 100%;
    height: 100%;
    z-index: 999;
    display: flex;
    align-items: center;
    justify-content: center;
    background: #2c3e50;
}

// your animation code (SpinKit used in this demo)
```
