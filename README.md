# Big Book of Words - Companion App

A fun, child-friendly companion app for the "Big Book of Words" visual dictionary. This app helps children aged 4-6 interact with the book through two engaging game modes.

## 🎮 What This App Does

The app has two simple games:
1. **Find the Page** - Shows a random page number for children to find in the book
2. **Find the Image** - Shows a random image that children need to locate

Both games feature fun slot-machine style animations and cheerful sound effects!

## 📱 How to Use the App

### For Parents/Teachers:
1. Open the app on your phone or tablet
2. Click either "Find the Page" or "Find the Image"
3. Watch the slot machine animation
4. Help your child find the page number or image in their book
5. Click "Back to Menu" to play again

### Sound Control:
- Click the speaker icon (🔊) in the top-right corner to turn sounds on/off

## 🛠️ Customization Guide for Beginners

Don't worry if you're not tech-savvy! Follow these simple steps to customize the app for your book.

### What You'll Need:
- A computer
- Your book's images in digital format (JPG or PNG files)
- A text editor (Notepad on Windows, TextEdit on Mac, or download [VS Code](https://code.visualstudio.com/) for free)

### Step 1: Download and Open the App File

1. Save the `index.html` file to your computer
2. Right-click on the file and select:
    - Windows: "Open with" → "Notepad"
    - Mac: "Open with" → "TextEdit"
    - Or open it in VS Code if you downloaded it

### Step 2: Add Your Background Image

The app currently has a purple gradient background. To add your custom background:

1. Find this line (around line 30):
```css
background: linear-gradient(135deg, #667eea 0%, #764ba2 100%);
```

2. Replace it with:
```css
background: url('background.jpg') center/cover;
```

3. Make sure your background image is named `background.jpg` and in the same folder as `index.html`

### Step 3: Set Your Page Range

The app randomly picks pages between 7 and 458. To change this:

1. Press `Ctrl+F` (Windows) or `Cmd+F` (Mac) to search
2. Search for "458 - 7"
3. You'll find this code (appears twice):
```javascript
randomPage = Math.floor(Math.random() * (458 - 7 + 1)) + 7;
```

4. Change the numbers:
    - Replace `458` with your book's last page number
    - Replace `7` with your book's first page number

Example: If your book goes from page 10 to 350:
```javascript
randomPage = Math.floor(Math.random() * (350 - 10 + 1)) + 10;
```

### Step 4: Exclude Specific Pages

Some pages might not have content (like chapter dividers). To exclude them:

1. Search for "excludedPages"
2. You'll find:
```javascript
const excludedPages = new Set([100, 150, 200, 250, 300, 350, 400]);
```

3. Replace the numbers with pages you want to skip:
```javascript
const excludedPages = new Set([15, 16, 45, 46, 89, 90]);
```

4. To exclude no pages, use:
```javascript
const excludedPages = new Set([]);
```

### Step 5: Add Your Book's Images

This is the most important part!

1. Create a folder called `images` in the same location as your `index.html` file
2. Copy all your book's images into this folder
3. Name them clearly (e.g., `ant.jpg`, `butterfly.jpg`, `cat.jpg`)

4. Search for "sampleImages" in the code
5. You'll find:
```javascript
const sampleImages = [
    '🐶', '🐱', '🐭', '🐹', '🐰', '🦊', '🐻', '🐼', '🐨', '🐯',
    // ... more emoji ...
];
```

6. Replace it with your image files:
```javascript
const sampleImages = [
    'images/ant.jpg',
    'images/butterfly.jpg',
    'images/cat.jpg',
    'images/dog.jpg',
    'images/elephant.jpg',
    // add all your images here
];
```

**Important Tips:**
- Use the exact filename including the extension (.jpg or .png)
- Put quotes around each filename
- Separate each with a comma
- Don't put a comma after the last image

### Step 6: Update the Image Display

To show your images properly:

1. Search for "font-size: 2em"
2. You'll find this code (appears twice):
```javascript
slotContent.innerHTML = `<span style="font-size: 2em;">${randomImage}</span>`;
```

3. Replace both instances with:
```javascript
slotContent.innerHTML = `<img src="${randomImage}" style="max-width: 180px; max-height: 180px;">`;
```

### Step 7: Customize Colors (Optional)

Want different colors? Here are easy changes:

**Change button color:**
1. Search for "background: #ff4444"
2. Replace `#ff4444` with:
    - Blue: `#4444ff`
    - Green: `#44ff44`
    - Orange: `#ff8844`
    - Pink: `#ff44ff`

**Change background:**
1. Search for "background: linear-gradient"
2. Try these alternatives:
```css
background: linear-gradient(135deg, #84fab0 0%, #8fd3f4 100%); /* Green-Blue */
background: linear-gradient(135deg, #fa709a 0%, #fee140 100%); /* Pink-Yellow */
background: linear-gradient(135deg, #30cfd0 0%, #330867 100%); /* Teal-Purple */
```

### Step 8: Save and Test

1. Save the file (`Ctrl+S` or `Cmd+S`)
2. Double-click the `index.html` file to open it in your browser
3. Test both game modes
4. Check on your phone by:
    - Uploading to GitHub Pages (see deployment instructions)
    - Or email the file to yourself and open on your phone

## 📁 File Organization

Your folder should look like this:
```
big-book-of-words/
│   index.html
│   background.jpg (optional)
│
└───images/
    │   ant.jpg
    │   butterfly.jpg
    │   cat.jpg
    │   dog.jpg
    │   ... (all your other images)
```

## 🔧 Troubleshooting

### "My images aren't showing!"
- Check that image filenames in the code match exactly (including capitals)
- Make sure images are in the `images` folder
- Verify the path starts with `images/`

### "The page numbers are wrong!"
- Make sure you changed both instances of the random number code
- Check that your first page number is smaller than your last page number

### "The app looks weird on my phone!"
- This is designed for portrait mode - try rotating your phone
- Clear your browser cache and reload

### "No sound is playing!"
- Check the speaker icon isn't muted (should show 🔊 not 🔇)
- Make sure your phone isn't on silent mode

## 💡 Extra Customization Ideas

### Change the App Title:
Search for "Big Book of Words" and replace with your book's title

### Change Button Text:
Search for "Find the Page" or "Find the Image" and replace with your preferred text

### Adjust Animation Speed:
Search for "duration = 3000" and change 3000 to:
- 2000 for faster (2 seconds)
- 5000 for slower (5 seconds)

## 🆘 Need More Help?

If you get stuck:
1. Double-check you followed each step exactly
2. Try copying the original file and starting fresh
3. Ask a tech-savvy friend or family member
4. The original code has no errors - if something breaks, undo your last change

Remember: You can always start over with a fresh copy of the original file!

## 📄 License

This app is created for personal/educational use with the "Big Book of Words" visual dictionary.
