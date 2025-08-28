Great enhancement adding the "Register Student" button and associated event handling! To further optimize and simplify the code, I recommend using event delegation instead of attaching individual listeners to each .register-btn. This approach improves performance, especially as the activities list grows, and ensures new buttons are handled automatically.

**Proposed change:**  
Replace the loop that attaches listeners to .register-btn with a single event listener on the parent container (e.g., activitiesList):

```javascript
activitiesList.addEventListener("click", (event) => {
  if (event.target.classList.contains("register-btn")) {
    const activityName = event.target.getAttribute("data-activity");
    const signupContainer = document.getElementById("signup-container");
    const activitySelect = document.getElementById("activity");
    if (activitySelect && signupContainer) {
      activitySelect.value = activityName;
      signupContainer.classList.remove("hidden");
    }
  }
});
``` 

This reduces DOM queries and improves scalability. Let me know if you want me to push this change or help with additional improvements!