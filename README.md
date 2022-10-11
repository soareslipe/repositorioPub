import React from "react";
import axios from "axios";

class App extends React.Component {

  constructor() {
    super();
    this.state = {
      selectedFile: '',
    }

    this.handleInputChange = this.handleInputChange.bind(this);
  }

  handleInputChange(event) {
    this.setState({
      selectedFile: event.target.files[0],
    })
  }

  submit() {
    const data = new FormData()
    data.append('file', this.state.selectedFile)
    console.warn(this.state.selectedFile);
    let url = "http://localhost:8000/pedido";

    axios.post(url, data, { // receive two parameter endpoint url ,form data 
    })
      .then(res => { // then print response status
        console.warn(res);
      })

  }
  render() {
    return (



      <div>
        <label>Upload your file</label>
        <input type='file' name='file' onChange={this.handleInputChange} />
        <button type="submit" onClick={()=>this.submit()}>Save</button>
      </div>

    )
  }
}



export default App
